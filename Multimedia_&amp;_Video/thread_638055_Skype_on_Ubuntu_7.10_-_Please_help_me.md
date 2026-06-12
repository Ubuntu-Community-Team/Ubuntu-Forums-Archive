---
title: "Skype on Ubuntu 7.10 - Please help me"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by dudi.dalal on 2007-12-11
Hi all

I'm newbie to to Linux so please forgive me if I describe my problem in non professional way, sorry for my poor English too.

I changed my OS from Windows 2000 to Ubuntu 7.10 having no problem to use applications at all (except the fact under my old box, Pentium III 733Mhz with 1G RAM, they run somehow a bit slow, but I can live with that)

I installed Skype 1.4 (as I got from the Synaptic manager, which installed also skype-common package)

I work fine with Skype (the sound was not as good as Windows, but again I leave with it)

After I install KDE and  XFCE and REMOVE them (Did it because I thought that might make my machine run faster)  Skype is stacked after Login showing white window. When I try closing the window it write me Skype is not responding ....

I try to remove the package and reinstall it, but without success.

I was very frustrated and try to install the new Beta 2.0 version. Well the Skype was able to login and to show me my contact list, but I was unable to perform a call or even a chat.

Before I used Linux Skype was serving me a lot.

Please help me use Skype again.   

Some more parameters:

My Kernel is:

2.6.22-14-generic

I checked the libs I got:
libc6
libqt4  (4.3.2-1)
alsa  (1.0.14-1)

---

### Post by kubug on 2007-12-11
It's a shot in the dark, but have you tried removing the .Skype directory in your home directory? It is hidden, so you will have to click on "Show Hidden Files" in nautilus.

Other than that, I tried upgrading from Skype 1.4 to 2.0 myself. It gave me problems because the 2.0 deb package if for 7.04 (feisty).

What you would have to do is totally remove all skype installations:

```

sudo apt-get remove skype*

```

then delete the .Skype directory

```

rm ~/.Skype

```

and then reinstall the 2.0 deb. 

If this didn't fix it, you may have messed up something somewhere by installing and removing those other desktops. 

That P3 should be fine, especially with 1GB of ram. Are you sure you have the right video driver?
That could make things somewhat slow. Other than that, if you use an old HDD that came make things slow as well.

---

### Post by SLA_leandrin on 2007-12-12
Try launching Skype form a console, and post the error message here...

---

### Post by dudi.dalal on 2007-12-12
Hi all

First thanks for your help !

1) First I tried to run skpe from command line No log was created to std out.

2) I tried your advice to remove the .Skype directory (under my home directory),

Also did:

```
apt-get purge skype
```

After that I installed the Skype 1.4 (from Synaptic package manager)

But now after I logged in, it tells me Server Connect Fail  (which is different then getting white Skype window, but still not helping)

I checked my connection to internet and it is Ok

3) did purge again, remove .Skype directory  and install Skype 2.0, Success to login, but now something very strange happened, I have no contact list, no credit

Do you have more suggestions ?

Thanks in advance

---

