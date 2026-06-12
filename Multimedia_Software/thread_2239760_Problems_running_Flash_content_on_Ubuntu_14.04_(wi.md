---
title: "Problems running Flash content on Ubuntu 14.04 (with unusual network activity)"
date: 2014-08-15
forum: Multimedia Software
---

### Post by JustSomeCanuck on 2014-08-15
Hello everyone,

If this thread sounds familiar, I had previously asked about it (in the Networking category). I thought I had fixed the problem, but it's still happening.

My computer is a Toshiba Satellite L840D notebook. I started with 12.04 installed and upgraded to 14.04 soon after.

I'll describe this using a YouTube video as the example, but this also applies to other sites with Flash content (games, for example). Whenever I click play, if I'm using the wireless, only a short amount of the video downloads, and then it stops completely and the loading circle appears. If I use an Ethernet cable, the whole video will download. In either case I can see that the network gets very busy sending data. I took this screenshot (using Ethernet cable) to explain:

[ATTACH=CONFIG]255510[/ATTACH]

Note that the total data sent is greater than the total received. Also, when I've been using either the cable or the wireless, people using other computers on my home network notice the Internet is very slow for them. These problems only appear when Flash is involved - anything else, even large downloads (like downloading the latest set of Ubuntu updates) work fine and don't show that network activity. I've tried using HTML5 (YouTube only) and disabiling the firewall (ufw) without success. Updating the Flash version didn't fix it either. I regularly update Ubuntu and the browser plugins (if needed).

Any ideas as to what could be causing this? I've tried everything I could think of.

Thanks.

---

### Post by TheFu on 2014-08-15
Tried a different browser?  I see a similar issue when using double-NAT networks.  To get around it, the youtube-dl program (in the repos) works great.

---

### Post by Yellow Pasque on 2014-08-15
Try clearing the Flash cache:
```
rm -r ~/.Flash_Player/*
```

---

### Post by JustSomeCanuck on 2014-08-23
Hello,

Sadly, clearing the Flash cache doesn't seem to have worked. I'd rather not use any other browsers, since it's more of an inconvenience than a major problem (and because I prefer Firefox). As I said, everything else works fine. I'll leave this thread open for a while to see if there are any more suggestions.

---

### Post by lah7 on 2014-08-24
Have you tried running Ubuntu 14.04 off a live CD/USB to see if it still happens? (Particularly to check if it still sends data, which is unusual)
You could also try another browser in the live session, to avoid inconveniently installing additional packages to your system.

This might narrow it down if it's purely as a result of the Ubuntu 12.04 upgrade with some packages, and not any other external factors.

You may wish to note that Firefox and Chromium browsers rely on the flash plugin externally, where Chrome has it's own version built-in.

Have you also tried purging (completely remove) and re-installing the Firefox/Flash packages?
```

sudo apt-get purge firefox flashplugin-installer
rm -r ~/.mozilla/firefox/
rm -r ~/.adobe/Flash_Player/
sudo apt-get install firefox

```
When Firefox prompts plug-ins are missing, follow the steps to install Flash once again.
**Note:** This will erase your Firefox configuration, export anything important first.

---

### Post by JustSomeCanuck on 2014-09-07
Latest update: I tried purging and reinstalling Firefox, and that worked for a short time. The network activity (sending) was still there, but the movies did fully load. Oddly, it never asked me to reinstall Flash or said anything about missing plugins. Restoring my backed-up settings made no difference. I'll check it using a live USB when I get a chance, but any other suggestions are always welcome.

It's actually the data sending that has me concerned (at first, I thought that might even be a virus, rare as they are on Linux).

---

### Post by Nistegmos on 2014-09-08
maybe you're getting hacked wirelessly

---

