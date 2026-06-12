---
title: "openvpn issue"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by adeelm on 2010-02-12
hi everyone,

             I am using ubuntu 9.10 and was installing openVPN on it. I did the following steps

**sudo apt-get install openvpn**
**sudo mkdir /etc/openvpn/easy-rsa/**
**sudo cp -r /usr/share/doc/openvpn/examples/easy-rsa/2.0/ /etc/openvpn/**
**cd /etc/openvpn/easy-rsa/easy-rsa**
**source vars**
**./clean-all**
**./build-dh**
[B]./pkitool --initca


After running ./pkitool --initca I get this line and it is continous.
and it keeps on going on and on. I have to abort this it.[/B]

and it is writen on this link below ./build-dh takes a long time but when I
run it it does not takes more then 30 sec.

[https://help.ubuntu.com/9.10/serverguide/C/openvpn.html](https://help.ubuntu.com/9.10/serverguide/C/openvpn.html)
string is too long, it needs to be less than  2 bytes long

Hopng for a solution from your side.

Thanks

Adeel

---

### Post by adeelm on 2010-02-12
The message that comes on to the terminal is this after running [B]./pkitool --initca


[/B][SIZE=4][COLOR=Red]string is too long, it needs to be less than  2 bytes long
[/COLOR][/SIZE][SIZE=4][COLOR=Red]string is too long, it needs to be less than  2 bytes long...[/COLOR][/SIZE]

---

### Post by LAD29 on 2010-07-27
Did you find a solution to this problem?

I have the same message except mine say 40 bytes long.

Any ideas?

PS. running Kubuntu 10.04 though.

---

### Post by yiun on 2010-09-23
I had the same problem and solved it by making the export-values shorter:
```
sudo vi /etc/openvpn/easy-rsa/vars
```

---

### Post by Oceanborn on 2011-02-20
> **yiun said:**
> I had the same problem and solved it by making the export-values shorter:
```
sudo vi /etc/openvpn/easy-rsa/vars
```

Actually, I just shortened KEY_COUNTRY value to two characters:

```
KEY_COUNTRY="UK"
```

instead of:

```
KEY_COUNTRY="Ukraine"
```

and that resolved the problem.

---

### Post by regala on 2012-01-06
> **Oceanborn said:**
> Actually, I just shortened KEY_COUNTRY value to two characters:

```
KEY_COUNTRY="UK"
```

instead of:

```
KEY_COUNTRY="Ukraine"
```

and that resolved the problem.

a little late, but just so you know UK is for United Kingdom in ssl key country codes... for Ukraine you need UA

---

