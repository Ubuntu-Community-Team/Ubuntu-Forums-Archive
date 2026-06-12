---
title: "OpenVPN---Unable to connect.."
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by satyam.m on 2013-08-03
For last few days, i have been trying to form openvpn connection on 12.04 but have been unable to do so.....

My .ovpn file reads something like following:

[HTML]
client 
dev tun 
tun-mtu 1428 
proto tcp 
remote 46.23.68.178 443 
remote uk1.vpnbook.com 443 
remote 46.23.68.178 80 
resolv-retry infinite 
nobind 
persist-key 
persist-tun 
float 
auth-user-pass 
comp-lzo 
verb 3 
cipher AES-128-CBC 
fast-io 
pull 
route-delay 2 
redirect-gateway 
mute 20 


<ca> 
-----BEGIN CERTIFICATE----- 
MIIDyzCCAzSgAwIBAgIJAKRtpjsIvek1MA0GCSqGSIb3DQEBBQUAMIGgMQswCQYD 
VQQGEwJDSDEPMA0GA1UECBMGWnVyaWNoMQ8wDQYDVQQHEwZadXJpY2gxFDASBgNV 
BAoTC3ZwbmJvb2suY29tMQswCQYDVQQLEwJJVDEUMBIGA1UEAxMLdnBuYm9vay5j 
b20xFDASBgNVBCkTC3ZwbmJvb2suY29tMSAwHgYJKoZIhvcNAQkBFhFhZG1pbkB2 
cG5ib29rLmNvbTAeFw0xMzA0MjQwNDA3NDhaFw0yMzA0MjIwNDA3NDhaMIGgMQsw 
CQYDVQQGEwJDSDEPMA0GA1UECBMGWnVyaWNoMQ8wDQYDVQQHEwZadXJpY2gxFDAS 
BgNVBAoTC3ZwbmJvb2suY29tMQswCQYDVQQLEwJJVDEUMBIGA1UEAxMLdnBuYm9v 
ay5jb20xFDASBgNVBCkTC3ZwbmJvb2suY29tMSAwHgYJKoZIhvcNAQkBFhFhZG1p 
bkB2cG5ib29rLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAyNwZEYs6 
WN+j1zXYLEwiQMShc1mHmY9f9cx18hF/rENG+TBgaS5RVx9zU+7a9X1P3r2OyLXi 
WzqvEMmZIEhij8MtCxbZGEEUHktkbZqLAryIo8ubUigqke25+QyVLDIBuqIXjpw3 
hJQMXIgMic1u7TGsvgEUahU/5qbLIGPNDlUCAwEAAaOCAQkwggEFMB0GA1UdDgQW 
BBRZ4KGhnll1W+K/KJVFl/C2+KM+JjCB1QYDVR0jBIHNMIHKgBRZ4KGhnll1W+K/ 
KJVFl/C2+KM+JqGBpqSBozCBoDELMAkGA1UEBhMCQ0gxDzANBgNVBAgTBlp1cmlj 
aDEPMA0GA1UEBxMGWnVyaWNoMRQwEgYDVQQKEwt2cG5ib29rLmNvbTELMAkGA1UE 
CxMCSVQxFDASBgNVBAMTC3ZwbmJvb2suY29tMRQwEgYDVQQpEwt2cG5ib29rLmNv 
bTEgMB4GCSqGSIb3DQEJARYRYWRtaW5AdnBuYm9vay5jb22CCQCkbaY7CL3pNTAM 
BgNVHRMEBTADAQH/MA0GCSqGSIb3DQEBBQUAA4GBAKaoCEWk2pitKjbhChjl1rLj 
6FwAZ74bcX/YwXM4X4st6k2+Fgve3xzwUWTXinBIyz/WDapQmX8DHk1N3Y5FuRkv 
wOgathAN44PrxLAI8kkxkngxby1xrG7LtMmpATxY7fYLOQ9yHge7RRZKDieJcX3j 
+ogTneOl2w6P0xP6lyI6 
-----END CERTIFICATE----- 
</ca> 


<cert> 
-----BEGIN CERTIFICATE----- 
MIID6DCCA1GgAwIBAgIBATANBgkqhkiG9w0BAQUFADCBoDELMAkGA1UEBhMCQ0gx 
DzANBgNVBAgTBlp1cmljaDEPMA0GA1UEBxMGWnVyaWNoMRQwEgYDVQQKEwt2cG5i 
b29rLmNvbTELMAkGA1UECxMCSVQxFDASBgNVBAMTC3ZwbmJvb2suY29tMRQwEgYD 
VQQpEwt2cG5ib29rLmNvbTEgMB4GCSqGSIb3DQEJARYRYWRtaW5AdnBuYm9vay5j 
b20wHhcNMTMwNTA2MDMyMTIxWhcNMjMwNTA0MDMyMTIxWjB4MQswCQYDVQQGEwJD 
SDEPMA0GA1UECBMGWnVyaWNoMQ8wDQYDVQQHEwZadXJpY2gxFDASBgNVBAoTC3Zw 
bmJvb2suY29tMQ8wDQYDVQQDEwZjbGllbnQxIDAeBgkqhkiG9w0BCQEWEWFkbWlu 
QHZwbmJvb2suY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCkTM/8E+JH 
CjskqMIwgYDrNCBTWZLa+qKkJjZ/rliJomTfVYwKwv1AHYYU6RHpCxS1qFp3BEKL 
vQlASuzycSv1FGnNiLmg94fqzzWdmjs1XWosnLqbOwxx2Ye/1WoakSHia0pItoZk 
xK7/fllm42+Qujri/ERGga5Cb/TfiP6pUQIDAQABo4IBVzCCAVMwCQYDVR0TBAIw 
ADAtBglghkgBhvhCAQ0EIBYeRWFzeS1SU0EgR2VuZXJhdGVkIENlcnRpZmljYXRl 
MB0GA1UdDgQWBBTDr4BCNSdOEh+Lx6+4RRK11x8XcDCB1QYDVR0jBIHNMIHKgBRZ 
4KGhnll1W+K/KJVFl/C2+KM+JqGBpqSBozCBoDELMAkGA1UEBhMCQ0gxDzANBgNV 
BAgTBlp1cmljaDEPMA0GA1UEBxMGWnVyaWNoMRQwEgYDVQQKEwt2cG5ib29rLmNv 
bTELMAkGA1UECxMCSVQxFDASBgNVBAMTC3ZwbmJvb2suY29tMRQwEgYDVQQpEwt2 
cG5ib29rLmNvbTEgMB4GCSqGSIb3DQEJARYRYWRtaW5AdnBuYm9vay5jb22CCQCk 
baY7CL3pNTATBgNVHSUEDDAKBggrBgEFBQcDAjALBgNVHQ8EBAMCB4AwDQYJKoZI 
hvcNAQEFBQADgYEAoDgD8mpVPnHUh7RhQziwhp8APC8K3jToZ0Dv4MYXQnzyXziH 
QbewJZABCcOKYS0VRB/6zYX/9dIBogA/ieLgLrXESIeOp1SfP3xt+gGXSiJaohyA 
/NLsTi/Am8OP211IFLyDLvPqZuqlh/+/GOLcMCeCrMj4RYxWstNxtguGQFc= 
-----END CERTIFICATE----- 
</cert> 


<key> 
-----BEGIN RSA PRIVATE KEY----- 
MIICXAIBAAKBgQCkTM/8E+JHCjskqMIwgYDrNCBTWZLa+qKkJjZ/rliJomTfVYwK 
wv1AHYYU6RHpCxS1qFp3BEKLvQlASuzycSv1FGnNiLmg94fqzzWdmjs1XWosnLqb 
Owxx2Ye/1WoakSHia0pItoZkxK7/fllm42+Qujri/ERGga5Cb/TfiP6pUQIDAQAB 
AoGANX508WQf9nVUUFlJ8LUZnnr4U2sEr5uPPNbcQ7ImTZm8MiMOV6qo/ikesMw5 
8qCS+5p26e1PJWRFENPUVhOW9c07z+nRMyHBQzFnNAFD7TiayjNk1gz1oIXarceR 
edNGFDdWCwXh+nJJ6whbQn9ioyTg9aqScrcATmHQxTit0GECQQDR5FmwC7g0eGwZ 
VHgSc/bZzo0q3VjNGakrA2zSXWUWrE0ybBm2wJNBYKAeskzWxoc6/gJa8mKEU+Vv 
ugGb+J/tAkEAyGSEmWROUf4WX5DLl6nkjShdyv4LAQpByhiwLjmiZL7F4/irY4fo 
ct2Ii5uMzwERRvHjJ7yzJJic8gkEca2adQJABxjZj4JV8DBCN3kLtlQFfMfnLhPd 
9NFxTusGuvY9fM7GrXXKSMuqLwO9ZkxRHNIJsIz2N20Kt76+e1CmzUdS4QJAVvbQ 
WKUgHBMRcI2s3PecuOmQspxG+D+UR3kpVBYs9F2aEZIEBuCfLuIW9Mcfd2I2NjyY 
4NDSSYp1adAh/pdhVQJBANDrlnodYDu6A+a4YO9otjd+296/T8JpePI/KNxk7N0A 
gm7SAhk379I6hr5NXdBbvTedlb1ULrhWV8lpwZ9HW2k= 
-----END RSA PRIVATE KEY----- 
</key>
[/HTML]


To connect I type on terminal: [HTML]openvpn file.ovpn[/HTML]

Sometimes I get connected and get a speed as pathetic as 1Kb/s.....:'(
Sometimes I can open some website for 10 seconds and next moment it's gone... :'(
Sometimes it shows it is connected (i.e Initialization seq completed at terminal) but no website opens... :'(
Lots of pains in my life..

Somebody must help me here...

---

### Post by satyam.m on 2013-08-03
I have saved this .ovpn file at Desktop and execute this file using command given above...

Sometimes speed goes down to 0.1 to 0.4 Kb/sec...and never recovers to normal... :-( :-(

---

