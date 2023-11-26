# Config Loader
Config Loader is a Go package designed to simplify the loading of configuration parameters for your applications. It utilizes the cleanenv library to read configuration from a YAML file, with added support for default values specified through environment variables.

Usage
Installation
```bash
go get -u github.com/yberikov/configLoader
```

yaml
Copy code
env: local
http_server:
  host: localhost
  port: 8080
  timeout: 4s
Config Struct
The Config struct defines the overall configuration, including an environment field (Env) and an embedded HTTPServer struct.


```golang
type Config struct {
	Env        string      `yaml:"env" env-default:"local"`
	HTTPServer HTTPServer  `yaml:"http_server"`
}
```
HTTPServer Struct
The HTTPServer struct contains fields for configuring the HTTP server, including Host, Port, and Timeout.
```golang
type HTTPServer struct {
	Host    string        `yaml:"host" env-default:"localhost"`
	Port    string        `yaml:"port" env-default:"8080"`
	Timeout time.Duration `yaml:"timeout" env-default:"4s"`
}
```



Dependencies
cleanenv: A package for reading environment variables into a struct in a clean and easy way.
