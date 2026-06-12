---
title: "Privoxy / TOR problem"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Trekrider58 on 2009-01-25
My ISP has blocked access to a website in the UK - currently trying to find out why as it is a legit site.

To get round the problem I have installed TOR. On my old Windows XP machine with TOR enabled I can get to the site with no problems.

I installed TOR on my main (Ubuntu) machine running Hardy and found I couldn't access _any_ site with TOR enabled. I was told that Hardy was known to have a problem with TOR and to upgrade to Intrepid which I did. I have installed TOR through Synaptic which also installed Privoxy at the same time. If I enable TOR I can now get to my usual websites with no problem but when I try to access the 'blocked' UK site I get a failure message from Privoxy.

Anyone any suggestions how to fix this? I hate having to use my old XP machine.

---

### Post by Dr Small on 2009-01-25
What is the failure message? Perhaps the site is offline, and that's why you can't access it.

---

### Post by Trekrider58 on 2009-01-25
I have just been checking out further and found that on my XP machine with TOR stopped I get the same '503' error from Privoxy that I get in Ubuntu with TOR enabled. I am using the TOR Button extension in Firefox under Ubuntu and now wonder if TOR is actually working correctly. The button must be doing something as with TOR disabled the link times out.

Other than the TOR button in Firefox is there any other way of controlling TOR and/or checking its status?

---

### Post by Trekrider58 on 2009-01-25
> **Dr Small said:**
> What is the failure message? Perhaps the site is offline, and that's why you can't access it.

The failure message is '503' and suggests that the site may just not be there but I know it is as I can access the site under XP with TOR enabled. Plus see my second post - any ideas?

---

### Post by Dr Small on 2009-01-25
HTTP 503 means "Service Unavailable".

But besides that, let's take a look at how you have configured Tor + Privoxy. There are alot of ways, but only one way works.

Ok, so first off, you have installed tor and privoxy. I know this much. We need to edit the privoxy config file in order to make it use Tor as the proxy. Use your favorite editor (with sudo) and edit "/etc/privoxy/config". At the top of the file, add this line:
```
forward-socks4a / localhost:9050 .
```

Start tor:
```
sudo /etc/init.d/tor start
```

Start Privoxy:
```
sudo /etc/init.d/privoxy start
```


I haven't used the torbutton in quite a spell, so I can't give you any instructions on that. So instead, you can either mess with the settings in it, or just manually configure the network (which is what I am about to tell you).

In Firefox: Edit > Preferences > Advanced > Network > Settings (button) > Manual Proxy Configuration.

Now, for the details. In the HTTP Proxy field, enter "127.0.0.1". In the port field, enter "8118". Check "Use this proxy server for all protocols".

Now, test and verify that Privoxy is working:
[http://config.privoxy.org/](http://config.privoxy.org/)

Now check and see if tor is working:
[http://whatismyip.org](http://whatismyip.org)


If everything works, then you are really using tor. If not, I'll have to look back and see what we missed.

---

### Post by Trekrider58 on 2009-01-25
> **Dr Small said:**
> 
Ok, so first off, you have installed tor and privoxy. I know this much. We need to edit the privoxy config file in order to make it use Tor as the proxy. Use your favorite editor (with sudo) and edit "/etc/privoxy/config". At the top of the file, add this line:
```
forward-socks4a / localhost:9050 .
```


Thanks Dr Small, Whilst you were going to the trouble to write this I was on the Privoxy website and found the following instructions:

'Open Privoxy's "config" file (look in /etc/privoxy/ or /usr/local/etc/) and add the line
forward-socks4a / 127.0.0.1:9050 .
to the top of the config file. Don't forget to add the dot at the end.'

I followed the above instructions and hey-presto it now works.:D

Is there a difference between 'localhost' and '127.0.0.1'?

Thanks again for your help.

---

### Post by Dr Small on 2009-01-25
> **Trekrider58 said:**
> Is there a difference between 'localhost' and '127.0.0.1'?
There is if localhost is not specified in /etc/hosts, but for the most part, no. You can use it interchangeably since localhost is the hostname for 127.0.0.1, the local loopback device. :) 

> **Trekrider58 said:**
> Thanks again for your help.

No problem. I'm glad I was able to be of some service to you. :)

Dr Small

---

### Post by Dr Small on 2009-01-25
By the way, just for the record, Privoxy is not required nor needed to use Tor. It is just there to act as a non-caching proxy that cuts out some advert junk, which does help the browsing experience. If you only want to use Tor by itself, you can just specify the SOCKS proxy in Firefox as "127.0.0.1" and port "9050" and you will be browsing by Tor alone :)

---

