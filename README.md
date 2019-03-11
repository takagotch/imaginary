### imaginary
---
https://github.com/h2non/imaginary

```js
var image
for operation in operations {
  image = operation.Run(image, operation.Options)
}
```

```sh
go get -u github.com/h2non/imaginary
go get -u gopkg.in/h2non/bimg.v1
curl -s https://raw.githubserconttent.com/h2non/bimg/master/preinstall.sh | sudo bash -
docker pull h2non/imaginary
docker run -p 9000:9000 h2non/imaginary -cors -gzip
docker run -p 9000:9000 -e "DEBUG=*" h2non/imaginary
sudo docker exec -it <containerIdOrName> bash
docker stop h2non/imaginary
git clone https://github.com/h2non/imaginary.git
heroku config:add BUILDPACK_URL=https://github.com/h2non/heroku-buildpack-imaginary.git
heroku config:add PKG_CONFIG_PATH=/app/vendor/vips/lib/pkgconfig
heroku git:remote -a your-application
git push heroku master
git clone https://github.com/h2non/imaginary.git
cf push -b https://github.com/yacloud-io/go-buildpack-imaginary.git imaginary-inst01 --no-stat
cf set-env imaginary-inst01 LD_LIBRARY_PATH /home/vcap/app/vendor/visp/lib
cf start imaginary-inst01
imaginary -concurrency 20
imaginary -p 8080
PORT=8080 imaginary
imaginary -p 8080 -concurrency 10
imaginary -p 8080 -enable-url-source
imaginary -p 8080 -mount ~/images
imaginary -p 8080 -enable-url-source-auth-forwarding
imaginary -p 8080 -enable-url-source -authorization "Bearer s3cr3t"
imaginary -p 8080 -enable-url-source -http-cache-ttl 31556926
imagenary -p 8080 -enable-placeholder -enable-url-source
imagenary -p 8080 -placeholder=placeholder.jpg -enable-url-source
imagenary -p 8080 -enable-url-signature -url-signature-key xxxxxxxxxxx
URL_SIGNATURE_KEY=xxxxxxxxxx imaginary -p 8080 -enable-url-signature
VIPS_CONCURRENCY=10 imaginary -p 8080 -concurrency 10
DEBUG=* imaginary -p 8080
DEBUG=imaginary imaginary -p 8080

curl -O "htttp://localhost:8088/crop?width=500&height=400&file=foo/bar/image.jpg"
curl -O "http://localhost:8088/crop?width=500&height=400&url=https://raw.github.usercontent.com/h2non/imaginary/master/testdata/large.jpg"
```

```go
signKey := "xxxx"
urlPath := "/resize"
urlQuery := "file=image.jpg&height=200&type=jpeg&width=300"

h := hmac.New(sha256.New, []byte(signKey))
h.Write([]byte(urlPath))
h.Write([]byte(urlQuery))
buf := h.Sum(nil)

fmt.Println("sign=" + base64.RawURLEncoding.EncodeToString(buf))
```

```
{
  "message": "Cannot read payload: no such file",
  "code": 1
}

{
  "imaginary": "0.1.28",
  "bimg": "1.0.5",
  "libvips": "8.4.1"
}

{
  "width": 550,
  "height": 740,
  "type": "jpeg",
  "space": "srgb",
  "hasAlpha": false,
  "hasProfile": true,
  "channels": 3,
  "orientation": 1
}

{
  "uptime": 1293,
  "allocatedMemory": 5.31,
  "totalAllocateMemory": 34.3,
  "goroutines": 19,
  "cpus": 8
}

[
  {
    "operation": string,
    "ignore_failure": boolean,
    "params": map[string]mixed,
  }
]

[
  {
    "operation": "crop",
    "params": {
      "width": 500,
      "height": 300
    }
  },
  {
    "operation": "rotate",
    "params": {
      "rotate": 180
    }
  },
  {
    "operation": "convert",
    "params": {
      "type": "webp"
    }
  }
]
```

```yml
version: "3"
services: 
  imaginary:
    image: h2non/imaginary:latest
    volumes:
      - images:/mnt/data
    environment:
      PORT: 9000
    command: -enable-url-source -mount /mnt/data
    ports:
     - "9000:9000"
```
