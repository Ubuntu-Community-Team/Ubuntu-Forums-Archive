---
title: "How to Install TOR in Karmic 9.10?"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by m3rc on 2010-02-16
I'm trying to setup Tor in Karmic. I went through a few guides already, including [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor). I added the repos in /etc/apt/sources.list and did "apt-get update". My sticking point is here:

```

#apt-get install tor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tor: Depends: tsocks but it is not installable
       Recommends: privoxy but it is not installable or
                   polipo (>= 1) but it is not installable
       Recommends: socat but it is not installable
E: Broken packages

```I installed tsocks manually from [http://sourceforge.net/projects/tsocks/](http://sourceforge.net/projects/tsocks/) and tested it: 
```

$tsocks
/usr/bin/tsocks: insufficient arguments

```I still get the same error message as before when doing "apt-get install tor", including the tsocks part. How do I fix this?

---

### Post by superprash2003 on 2010-02-17
[http://www.torproject.org/easy-download.html.en](http://www.torproject.org/easy-download.html.en)

---

### Post by m3rc on 2010-02-17
Thanks superprash2003. That's not my issue, though. I have the package sources configured correctly. My problem is that Tor depends on tsocks, but I installed tsocks and Tor still won't install. I've read plenty of forum posts about people upgrading to Karmic and having Tor work, but not any from people installing Tor fresh on Karmic. Does anyone have any suggestions?

---

### Post by m3rc on 2010-02-18
Wow, nvm. I didn't have the Universe repos enabled lol. If you're having the same problem, go to System-->Administration-->Software Sources and in the "Ubuntu Software" tab, check "Community-maintained open source software (Universe)". 
Close, run the updates, then "sudo apt-get install tor."

---

### Post by BillinDetroit on 2010-04-18
Important to note the 'fixed' Polipo config file offered on the Tor website. It's just a teeny-tiny link ... but man, what a difference!

---

