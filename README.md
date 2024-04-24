# cloudflare-docker-proxy

![deploy](https://github.com/soulwhisper/cloudflare-docker-proxy/actions/workflows/deploy.yaml/badge.svg)

> If you're looking for proxy for helm, maybe you can try [cloudflare-helm-proxy](https://github.com/ciiiii/cloudflare-helm-proxy).

## Deploy
[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/soulwhisper/cloudflare-docker-proxy)

1. create an cloudflare **API Token** first (token ONLY SHOW ONCE), **Account ID** is needed. (Account ID is different from Login ID. If Account ID **Not Found**, create an **Application** in **cloudflare workers** page first.)
2. fork this project
3. modify the link of the above button to your fork url
4. modify **routes** according to your **domain** as follow: (in file `src/index.js`)
   ```javascript
   const routes = {
     "docker-proxy.yourdomain.com": "https://registry-1.docker.io",
     "quay-proxy.yourdomain.com": "https://quay.io",
     "gcr-proxy.yourdomain.com": "https://gcr.io",
     "ghcr-proxy.yourdomain.com": "https://ghcr.io",
     "k8s-proxy.yourdomain.com": "https://registry.k8s.io",
   };
   ```  
5. click the button, you will be redirected to the deploy page.
6. do the following steps:
  - host your domain DNS on cloudflare
  - Click **Triggers** in the _worker page_ to show **Custom Domains** and **Routes** info.
  - add all domains (which config in _step 4_. eg: `docker-proxy.yourdomain.com`, `quay-proxy.yourdomain.com` etc.) to **Custom Domains** of the worker you have deployed. 

## Config Docker mirrors
modify `/etc/docker/daemon.json`, add **registry-mirrors** as follow:
    ```javascript
    {
        "registry-mirrors": ["https://docker-proxy.yourdomain.com"]
    }
    ```
2. restart docker daemon
   };
   ```

