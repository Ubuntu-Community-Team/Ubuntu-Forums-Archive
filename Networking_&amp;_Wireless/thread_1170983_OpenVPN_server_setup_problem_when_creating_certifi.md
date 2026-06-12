---
title: "OpenVPN server setup problem when creating certificate"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by chuugokujin on 2009-05-26
Ubuntu 9.04 64bit

I was setting up OpenVPN according to this tutorial
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

and there is a problem when I creating my certificate. The tutorial says I should do:
[COLOR="Lime"]cd /etc/openvpn/easy-rsa/ ## move to the easy-rsa directory
sudo chown -R root:admin .  ## make this directory writable by the system administrators
source ./vars ## execute your new vars file
./clean-all  ## Setup the easy-rsa directory (Deletes all keys)
./build-dh  ## takes a while consider backgrounding
./pkitool --initca ## creates ca cert and key
./pkitool --server server ## creates a server cert and key
cd keys
openvpn --genkey --secret ta.key  ## Build a TLS key
cp server.crt server.key ca.crt dh1024.pem ta.key ../../[/COLOR]

but whenever I try:
*source ./vars*
the shell gives me back:
[COLOR="Red"]NOTE: If you run ./clean-all, I will be doing a rm -r on /etc/openvpv/easy-rsa/keys[/COLOR]
I ignored it and tried the next line:
*sudo ./clean-all*
it then says:
[COLOR="Red"]Please source the vars script first (i.e. "source ./vars")[/COLOR]
It looks like source ./vars hasn't been succeeded.

Could anyone help me?

---

### Post by gombadi on 2009-05-26
> 
but whenever I try:
source ./vars
sudo ./clean-all

it then says:
Please source the vars script first (i.e. "source ./vars")
It looks like source ./vars hasn't been succeeded.

Could anyone help me? 


The easiest way is to
```
sudo su -
``` to become root and run all the commands in one environment without sudo. The problem is you are sourcing the file in your environment and then using sudo to switch users into a different environment and in the new environment it can not find the sourced vars file.

or

create the keys in your home directory - do not need to use sudo and then copy the key files to the correct place - will need sudo for this part.

---

### Post by chuugokujin on 2009-05-27
Thank you so much gombadi, problem solved!

---

### Post by NileI on 2010-03-30
[FONT=Arial][SIZE=2]Hi Guys,

Sorry to bring up a old thread, i am having problems with this. I have tried the above.

```

/etc/openvpn/easy-rsa/easy-rsa$ source ./vars sudo ./clean-all
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/easy-rsa/keys

```Any Ideas?

Have also tried it as root...
```

root@vpn:/etc/openvpn/easy-rsa/easy-rsa# source ./vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/easy-rsa/keys
root@vpn:/etc/openvpn/easy-rsa/easy-rsa# 

```
Nile[/SIZE][/FONT]

---

### Post by NileI on 2010-03-30
bump?

Really do need some help with this.

---

### Post by gombadi on 2010-03-30
> 
Sorry to bring up a old thread, i am having problems with this. I have tried the above.

```


/etc/openvpn/easy-rsa/easy-rsa$ source ./vars sudo ./clean-all
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/easy-rsa/keys

```


What is the problem you are having?

The message you are seeing is a standard warning that the file echos to he user. it is a few lines in the vars file -

```

# Issue rm -rf warning
echo NOTE: If you run ./clean-all, I will be doing a rm -rf on $KEY_DIR


```

All the rest of the vars file contains export commands for environment variables.

---

### Post by NileI on 2010-03-31
Hi There,

Thank you for clearing that up for me. I wasn't sure if because that message came up, the code didn't run. Sorry - im new to ubuntu!

Thanks,
Nile

---

