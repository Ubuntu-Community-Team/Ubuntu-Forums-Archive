---
title: "Cannot disable proxy"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by yuppienet on 2009-02-08
Hello all,

I have a problem with my laptop proxy settings. I am using ubuntu 8.10 and I use my laptop in my office, where a proxy must be configured. But when I return home and try to disable my proxy, it just doesn't.

The way I disable my proxy is by System / Preferences / Network Proxy:
In the proxy configuration tab, I select Direct internet connection (in my office I would select manual proxy configuration)

After I do that I open a terminal and check if the http_proxy is still there. Bizarrely, it is.
```

[bahamut]david@bahamut ~ $ env | grep http
http_proxy=http://x.y.z.q:3954/

```

It's very annoying to unset this variable _every_ time that I open a new console. So, what am I missing here?

Thanks for your help,
David

---

### Post by houcem on 2009-02-14
Try editing the config file /etc/apt/apt.conf

run sudo gedit /etc/apt/apt.conf

clear the file then type the following before saving

acquire::http:: proxy "false";

this will tet you use apt-get, synaptics...without proxy but for  other things I don't know I'm having the same problem. If someone else could help us...

---

### Post by yuppienet on 2009-02-14
Hi,

I tried that and apt-get still tries to connect thru proxy.
I erased the file and no luck either.

I have just discovered the location of the http_proxy value. It is on /etc/environment. I commented the http_proxy line and now it's working ok.

So now I would like to know: why didn't it change automatically when I set 'direct internet connection' on my proxy preferences? Bug?

Cheers

---

### Post by houcem on 2009-03-16
Probably yes I had the same problem.

---

### Post by cong06 on 2009-10-12
> **houcem said:**
> Try editing the config file /etc/apt/apt.conf

acquire::http:: proxy "false";

an extra space threw me off. try:
```
acquire::http::proxy "false";
```

> **yuppienet said:**
> I have just discovered the location of the http_proxy value. It is on /etc/environment. I commented the http_proxy line and now it's working ok.

So now I would like to know: why didn't it change automatically when I set 'direct internet connection' on my proxy preferences? Bug?

Same also.
Someone should write a bug report...

---

### Post by khatru82 on 2009-10-24
HI,
I resolved unsetting the environment variable http_proxy. After reboot, I didn't find the proxy settings anymore. Anyway, i think it is a real ubuntu bug since resetting proxy with System>Preferences didn't work.

---

### Post by actionist on 2010-03-05
I have the same problem. I am now unable to connect to my wired internet connection. Could any of you give me instructions in more detail about 'unsetting http_proxy' which seems to work, from what i can make out from previous posts.  Thanks.

---

### Post by cong06 on 2010-03-06
I'm not sure if this is related, but I noticed that if you start up "gconf-editor" and change some settings, these settings are different from setting gnome settings with gconftool:
```

gconftool -s /system/http_proxy/use_proxy -t bool true

```

---

### Post by ajkd on 2010-07-27
I am not sure this will work or not. But It worked for me.

system -> administration -> synaptic Package Manager -> setting -> preferences 
click network and  check direct connection to network

---

### Post by Pronker on 2011-03-17
@ajkd: it didn't for me.
@cong06: worked for me too... just seems like a bit of a stupid solution! I can't believe this bug is so old!!

---

### Post by sachieps on 2011-08-30
I had the same problem as yuppienet in Natty Narwhal. 
Fixed it by editing /etc/apt/apt.conf as houcem suggested with cong06s modification.
Cleared apt.conf file and added 
```
acquire::http::proxy "false";
```
before saving it.

---

### Post by creatron on 2011-11-12
Run
> sudo echo $http_proxy (enter)
if the variable is set like something
http_proxy=http://192.168.1.40:3128  reset the system variable with
> sudo http_proxy= (enter)

run 
> sudo echo $http_proxy (enter)
again

Do the same with $ftp_proxy

If the proxy is removed from 
   /etc/apt.conf                AND  
   /home/"user"/desktop/bash.bach.rc 
it should work

---

### Post by brewbuntu on 2012-01-12
Total noob here... but I thought I was having this problem too. 

For me, I had mistakenly ticked Automatic Proxy Configuration instead of Direct Internet Connection in System Settings>Network Proxy. Once I switched that back and clicked Apply System Wide then  Terminal stopped trying to use the work proxy.

Silly... I know, but it might be of some use to other people that stumble across this thread as I did. 

**System Settings>Network Proxy -> Select Direct Internet Connection**

---

