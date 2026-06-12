---
title: "Proxy, skype, no loging in"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by Dafydd on 2006-07-11
Hi
I'm on a university network which uses a proxy. I've set

1) preferences/network/default applications etc to use mozilla firefox with the university proxy settings.
2) i've tried http and https export with the proxy settings.


Despite this i still cannot get skype to login. The silly thing is that linux skype requires you to login to change proxy settings....

Has anyone got an ideas?

cheers
dafydd

---

### Post by kolesarm on 2006-10-08
i've tried the same, exported http & https proxies, set system > preferences > network proxy, but to no avail. trouble is that you need to be logged in in order to change the settings, it appears to me.

i'm running out of ideas..

---

### Post by kolach on 2006-11-13
There is a solution.

But not the best one :(

You must edit your shared.xml file to add proxy settings there.
This file is in your home/.Skype directory

The general solution is to have the Skype working
on Windows and then to compare the shared.xml files.

In my case I had to add section

      <HttpsProxy>
        <Addr>26.8.1.229:3128</Addr>
        <Enable>1</Enable>
        <Pwd>RmhjsdfsdQ=</Pwd>
        <User>kolach</User>
      </HttpsProxy>

in the <Connection> scope of the file.

the problem was with password. It seemed to be encrypted.
That is why I used Windows Skype installation to figure it out. 
Then just copied the section to Linux.

---

### Post by imvik on 2007-06-24
I tried modifying the shared.xml file but that file doesn't seem to exist on in my Skype directories!

Is Skype not installed correctly or is there some other problem? I tried reinstalling it but I still can't find the file.

Anyone? Help!

---

### Post by kolach on 2007-06-24
I have nothing to add. I have 3 computers with Windows and Linux installed and everywhere there is the shared.xml file that I've mentioned above. 
There might be some changes in new version of skype. My is 1.3 and the latest one (for Linux) is 1.4. 

I suggest you to have it working on Windows, then look at every configuration file to find the proxy settings, and try to understand how to apply it to Linux version.

---

### Post by ardovm on 2008-05-29
My favourite workaround is to add a default gateway:

```
$ sudo route add default gw proxy.server.ip.address
```

Skype will try to follow the default route for some seconds, and then correctly connect through the proxy.

This bug, for what I know, has always been in the Linux version of Skype. :-(

---

### Post by kolach on 2008-05-30
> **ardovm said:**
> My favourite workaround is to add a default gateway:

```
$ sudo route add default gw proxy.server.ip.address
```

Skype will try to follow the default route for some seconds, and then correctly connect through the proxy.

This bug, for what I know, has always been in the Linux version of Skype. :-(
wow! default route - my respect!

Now, as soon as I start having problems with all that authenticated proxy servers, I just change the company I'm working in :))))

---

### Post by ardovm on 2008-05-30
> **kolach said:**
> wow! default route - my respect!

Now, as soon as I start having problems with all that authenticated proxy servers, I just change the company I'm working in :))))
Ahem... sorry, I didn't get it.  :oops:

What I wanted to say is that you need to set a default route for your system. You don't need an actually working gateway: you just need to tell Linux that you have one, even if it's not working. Skype will then work through the proxy, after seeing that the default route takes nowhere.

---

### Post by kolach on 2008-05-30
No offence - good advice!

---

