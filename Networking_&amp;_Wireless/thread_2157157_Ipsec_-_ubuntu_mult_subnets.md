---
title: "Ipsec - ubuntu mult subnets"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by edudneto on 2013-06-24
I am setting up ipsec

But I'm struggling in a tunnel ipsec confiuração ..

but it only creates a route to the first network, I do not understand why not create a second network route.

openswan  version = 2.6.37-3 amd64

Follow the configuration file bellow

config setup
    interfaces=%defaultroute
    klipsdebug=none
    plutodebug=none
    uniqueids=yes
    protostack=netkey

conn TIM_GGRJO03
 auto=start
 type=tunnel
 keylife=1h                         # Intervalo de renegociacao de associacao de seguraca IPsec: 3600s
 ikelifetime=1440m               # Intervalo de renegociacao de associacao de seguranca IKE: 1440
 authby=secret                   # ipsec.secret   : PSK "*******"
 keyexchange=ike
 phase2=esp                              # Protocolo do IPSEC fase 2: ESP
 ike=aes256-sha1-modp1024         # Algoritmo fase 1: AES-256, Hash: SHA1, Grupo 2
 phase2alg=aes256-sha1;modp1024  # Fase 2:  Altoritmo cripto: AES-256, Hash: SHA1, Grupo 2
 pfs=yes                                   # PFS (Perfect Forward Secrecy) Habilitado
 aggrmode=no                         # Agressive mode desabilitado
 left=200.61.2.117                   # Gateway CEABS eth0
 leftsourceip=172.16.1.116        # IP rede interna CEABS eth1
 leftsubnet=172.16.0.0/16        # Range subnet CEABS
 right=200.40.228.33                #200.40.229.33       # Gateway TIM
 **rightsubnets={10.162.0.0/18,10.204.15.72/29} **


how are the routes
Destino         Roteador        MÃ¡scaraGen.    OpÃ§Ãµes MÃ©trica Ref   Uso Iface
200.61.2.112    0.0.0.0         255.255.255.240 U     0      0        0 eth0
**10.162.0.0      0.0.0.0         255.255.192.0   U     0      0        0 eth0                    <--- only this was create when start ipsec **
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         200.61.2.113    0.0.0.0         UG    100    0        0 eth0


**10.204.15.72/29** --this network don´t appeared

can someone help me. thanks

---

