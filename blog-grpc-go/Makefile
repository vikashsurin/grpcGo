gen:
	protoc protos/test.proto --go-grpc_out=./protos
	protoc protos/auth.proto --go-grpc_out=./protos
	protoc protos/user.proto --go-grpc_out=./protos
	protoc protos/blog.proto --go-grpc_out=./protos


	protoc protos/test.proto --go_out=./protos
	protoc protos/auth.proto --go_out=./protos
	protoc protos/user.proto --go_out=./protos
	protoc protos/blog.proto --go_out=./protos
ser:
	   go run server/*.go
cl:
	 go run client/*.go

certgen:
	cd cert; ./gen.sh; cd ..


grpcproxy:
	grpcwebproxy \
		--server_tls_cert_file=envoy/x509/server_cert.pem \
		--server_tls_key_file=envoy/x509/server_key.pem \
		--server_tls_client_ca_files=envoy/x509/ca_cert.pem \
		--backend_addr=localhost:5000 \
		--backend_tls_noverify \
		--allow_all_origins
# envoyProxy:
# 	cd envoy; envoy -c envoy.yaml
envoyProxy:
	cd envoy; func-e run -c envoy.yaml 