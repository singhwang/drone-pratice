## Kubernetes集群开启RBAC权限:
```
kubectl create clusterrolebinding default-cluster-admin \
  --clusterrole=cluster-admin \
  --serviceaccount=default:default
```

## 使用Docker镜像快速搭建GitLab社区版本:
```
docker run -d \
-p 80:80 -h gitlab \
--name gitlab --restart always \
-v /data/gitlab/config:/etc/gitlab \
-v /data/gitlab/logs:/var/log/gitlab \
-v /data/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:9.0.0-ce.0

vi /data/gitlab/config/gitlab.rb
external_url "http://{本机IP}"(80端口可用的情况下)
external_url "http://{本机IP}:{端口}"(自定义端口情况下)
nginx['listen_port'] = 80
docker restart gitlab
```
