---
title: "Dante server doesn't work"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by iksyos on 2009-01-12
Hi to all,
I would like to use Dante SOCKS server on linux and windows clients that use Dante as proxy.
Now i can't set properly Dante server. I did:

```
sudo apt-get install dante-server
```

on future proxy, then i start to configure. My configuration is:

```

logoutput: stderr /var/log/danted.log
internal: wlan0 port=1080 #AP external interface
external: wlan1 #interface on AODV network
method: none #only for try
user.privileged: root
user.notprivileged: nobody
client pass {
    from: 0.0.0.0/0 to: 0.0.0.0/0
    log: connect disconnect
}
pass {
    from: 0.0.0.0/0 to: 0.0.0.0/0
    command: connect udpassociate
    log: connect disconnect
}

```

after configuration i do:

```
sudo /etc/init.d/danted start
```

and it start properly, infact if i do:

```
netstat -n -a
```

i can see:

```
tcp  myaddress:1080    LISTEN
```

Now i set up my client, then i download freecap for windows and i set up firefox. When i try to connect using firefox i can't connect to the proxy.
On firefox browser appears the message: "Connection refused by proxy!"

Could you help me?

---

### Post by kbutcher5 on 2009-02-02
Could you start the server and type:
```

ps -fe | grep danted

```

---

### Post by iksyos on 2009-02-04
the result is this:

```
1000   7803  7557  0 16:00 pts/0    00:00:00 grep danted
```

---

### Post by kbutcher5 on 2009-02-04
Try this:
```

tail /var/log/danted.log

```

---

