---
title: "Flash: YouTube works, The Daily Show doesn't."
date: 2008-10-12
forum: Multimedia Software
---

### Post by sstecken on 2008-10-12
I have flashplugin-nonfree 9.0.124.0 installed for Firefox 3.0.3 on Hardy 8.04.  YouTube works fine, but The Daily Show ([http://www.thedailyshow.com](http://www.thedailyshow.com)) doesn't work.  Other sites do not work as well, and restarting Firefox does nothing.  The flash does not load, just a blank area where the flash should be.

Any ideas on how to fix this?  Am I missing a certain plugin?

---

### Post by simoncullen on 2009-01-15
bump . . . same problem.

---

### Post by jocheem67 on 2009-01-15
No problems here, using flash 10 on 32bit....

Can't you upgrade to 10 ?

---

### Post by simoncullen on 2009-01-15
Thanks.

I'm on 64bit.  I've just had some luck with the 64bit Alpha from Adobe:[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Seem to be working well, though rather high CPU utilisation, as usual.

---

### Post by mjec on 2009-04-11
I have the same issue with both Flash 10 Alpha and nspluginwrapper'd flash. With Flash 10 dmesg gives:

```
[****] npviewer.bin[7158]: segfault at c ip 00000000f66a2333 sp 00000000fffa2130 error 4 in libplds4.so.0d[f66a1000+2000]
```

which crashes firefox.

nspluginwrapper doesn't crash the browser but doesn't load the video at all - I get a transparent flash object.

Any assistance will result in much love. Happy to take advice on how to further debug this too...

---

### Post by gandaran on 2009-04-12
> **mjec said:**
> I have the same issue with both Flash 10 Alpha and nspluginwrapper'd flash. With Flash 10 dmesg gives:

```
[****] npviewer.bin[7158]: segfault at c ip 00000000f66a2333 sp 00000000fffa2130 error 4 in libplds4.so.0d[f66a1000+2000]
```

which crashes firefox.

nspluginwrapper doesn't crash the browser but doesn't load the video at all - I get a transparent flash object.

Any assistance will result in much love. Happy to take advice on how to further debug this too...
you should remove nspluginwrapper if you are using the 64-bits beta flash, nspluginwrapper is for use with 32-bits flash on 64-bits ubuntu.

---

### Post by bwana on 2009-04-25
> **jocheem67 said:**
> No problems here, using flash 10 on 32bit....

Can't you upgrade to 10 ?

I'm on Ubuntu 8.10-64, with flash 10 and I have no problems with any site I've come across, except for the dailyshow (no image or sound - as described by others).

---

### Post by wolfen69 on 2009-04-25
> **bwana said:**
> I'm on Ubuntu 8.10-64, with flash 10 and I have no problems with any site I've come across, except for the dailyshow (no image or sound - as described by others).

daily show works for me.

---

### Post by luisella on 2010-04-16
> **gandaran said:**
> you should remove nspluginwrapper if you are using the 64-bits beta flash, nspluginwrapper is for use with 32-bits flash on 64-bits ubuntu.

Thanks, this worked for me as well. The dailyshow wasn't playing and sometimes youtube showed the old interface on which mouse clicks were not working. That was beacuse I installed the new flash 10 without uninstalling nspluginwrapper.

To fix it I had to uninstall the nspluginwrapper package (which also uninstalls a dependent package plugin). Then reinstall flash10 for 64 bit linux ( [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html) ) by just copying the libflashplayer.so file into /usr/lib/mozilla/plugins.

---

### Post by Stagger Lee on 2010-05-03
Hi, I have been fighting with this exact same problem for hours, after updating to Lucid. 
I finally found a solution that is not reported anywhere else, and interestingly is not flash-related, so I thought I'd share for anyone who may have the same issue.
I too was blaming some Flash plugin update, but as it turns out, I was wrong. What did the trick was changing the DNS settings. I typed 
```
sudo  /etc/resolv.conf
```
and therein substituted the default address (192.168.1.1) with the Google Public DNS. Now I can view the Daily Show, both in Firefox 3.6 and Google Chrome (neither worked before). Go figure. 

Hope that helps - greetings from Italy :)

---

### Post by unntrlaffinity on 2010-05-05
> **luisella said:**
> Thanks, this worked for me as well. The dailyshow wasn't playing and sometimes youtube showed the old interface on which mouse clicks were not working. That was beacuse I installed the new flash 10 without uninstalling nspluginwrapper.

To fix it I had to uninstall the nspluginwrapper package (which also uninstalls a dependent package plugin). Then reinstall flash10 for 64 bit linux ( [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html) ) by just copying the libflashplayer.so file into /usr/lib/mozilla/plugins.

Doesn't this disable Hulu?  Hulu does not appear to work with Linux and 64-bit Flash.

For me fixing one appears to disable the other, for different reasons.

Is there a way to have both?  Right now the Daily Show is the only site that doesn't work for me.  YouTube, Hulu, and other Flash sites work fine.  I'm almost resigned to simply watching the Daily Show via my Windows XP Virtualbox image.

---

### Post by asdir on 2010-06-12
> **Stagger Lee said:**
> Hi, I have been fighting with this exact same problem for hours, after updating to Lucid. 
I finally found a solution that is not reported anywhere else, and interestingly is not flash-related, so I thought I'd share for anyone who may have the same issue.
I too was blaming some Flash plugin update, but as it turns out, I was wrong. What did the trick was changing the DNS settings. I typed 
```
sudo  /etc/resolv.conf
```
and therein substituted the default address (192.168.1.1) with the Google Public DNS. Now I can view the Daily Show, both in Firefox 3.6 and Google Chrome (neither worked before). Go figure. 

Hope that helps - greetings from Italy :)

Thanks, Stagger Lee, that resolved[ my issues]("http://ubuntuforums.org/showthread.php?p=9450177#post9450177"). Though, it should probably have been

```
sudo gedit /etc/resolv.conf
```

Also, if you use 

```
sudo /etc/init.d/networking restart
```

you won't have to have a restart of the system.

Anyway, thanks from Germany to Italy. :-D

---

