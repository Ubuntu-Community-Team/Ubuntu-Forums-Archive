---
title: "External Ip of a router"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by A_M_S on 2009-09-30
Hello.

How can i get the ip of the external interface (Internet interface) of a router from the cli?


tnx.

---

### Post by Krydox on 2009-09-30
You can go to [http://whatismyipaddress.com/]("http://whatismyipaddress.com/")

It's also on your router's status page with most devices.

---

### Post by A_M_S on 2009-09-30
Tnx for the reply, but that don't solve my problem.
what i need is to get the router ip from the CLI.

---

### Post by Krydox on 2009-09-30
You mean your router IP for setup? is usually the same as the gateway, you can try using ifconfig or route.

---

### Post by A_M_S on 2009-09-30
> **Krydox said:**
> You mean your router IP for setup? is usually the same as the gateway, you can try using ifconfig or route.

No.

What i want is a way to get my external IP address (the internet address) using the CLI.

I found this:

[http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html](http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html)

Just for curiosity, is there any way to do the same?
Tnx

---

### Post by peculiar penguin on 2009-09-30
```
wget -q -O - http://whatismyip.org
```

---

### Post by starcannon on 2009-09-30
*deleted by starcannon*
I didn't fully understand what the OP wanted. Sorry

---

### Post by Rytron on 2009-09-30
> **peculiar penguin said:**
> ```
wget -q -O - http://whatismyip.org
```

Very smart method!

:P

Can this be amended so the output looks something like this:
##.##.##.# Rambo@HQ:~$ 

So that there is a gap between the IP address and the username!

---

### Post by A_M_S on 2009-09-30
> **peculiar penguin said:**
> ```
wget -q -O - http://whatismyip.org
```

Tnx!!

---

### Post by Paddy Landau on 2009-10-01
> **Rytron said:**
> Can this be amended so the output looks something like this:
##.##.##.# Rambo@HQ:~$ 
In your bash profile (.bashrc):
```
if [[ -z "${IPADDRESS}" ]]
then
    export IPADDRESS=$( wget -qO - http://whatismyip.org/ )
fi
export PS1="${IPADDRESS} ${USER}:\w\$ "
```

---

