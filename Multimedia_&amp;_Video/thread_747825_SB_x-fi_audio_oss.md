---
title: "SB x-fi audio oss"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by hashi856 on 2008-04-06
I'm running ubuntu 7.10. I just installed it yesterday. I have a sound blaster x-fi sound card. I found This forum [http://ubuntuforums.org/showthread.php?p=4655104](http://ubuntuforums.org/showthread.php?p=4655104), and it was very helpful. But after the last step, the terminal gave me this error message.

oss build environment set up for REGPARM kernels

      c library headers (glibc-devel or build-essentials)

Error: The above Linux package(s) seem to be missing from your system. Please instal them and then try to install oss again

I followed the directions at the end of the message telling me how to download the needed packages but is said that it couldn't find them.
Where do I get those packages from? How do I fix this?

Here's a screenshot of the terminal [http://s218.photobucket.com/albums/cc73/hashi856/?action=view&current=asdf-1.png](http://s218.photobucket.com/albums/cc73/hashi856/?action=view&current=asdf-1.png)

[IMG]http://s218.photobucket.com/albums/cc73/hashi856/?action=view&current=asdf.png[/IMG]

---

### Post by tubasoldier on 2008-04-07
I wasn't sure what yoru issue was until I really looked at your screenshot.

You are trying to install build-essentials
You should install build-essential
Remove the 's' from the end.

```
sudo apt-get install build-essential
```

It should be in the main repository.

Hope this clears things up!



Also, I'm not sure if you heard about Creative and their drivers. Its a good thing that you get at least something form the open source community. They have been promising native linux drivers for nearly a year and a half now, i believe. Too long for my taste to purchase one.

---

### Post by hashi856 on 2008-04-07
thnks, removing the "s"'s fixed the problem with the command prompt, but unfortunately didn't help my problem in the long run. Everything happened like it was supposed to, but there was still no sound when I rebooted. Is there any hope?

---

### Post by tubasoldier on 2008-04-07
I don't have an X-fi myself. This driver is still considered "Alpha" stage, which is pretty hit and miss as it is. As things are now you will probably never see anything from Creative themselves although they have been promising it for so long. OSS is your best bet. 

If you haven't heard of the creative user revolt (happened last weekend) then Google "daniel_k creative". From what I understand the drivers for Vista are pretty bad as well.

---

### Post by hashi856 on 2008-04-07
so basicly I'm screwed

---

### Post by wolfen69 on 2008-04-07
if you use 64bit ubuntu there are beta drivers available from creative. go here [http://us.creative.com/support/downloads/](http://us.creative.com/support/downloads/)  and enter your card info. if you dont see a linux driver, try another version of x-fi, as i know they are available.

also, go here [http://us.creative.com/contactus/mailto/sitefeedback.asp](http://us.creative.com/contactus/mailto/sitefeedback.asp)  and make your voice be heard. let creative know that linux users want better driver support. i just did.

---

### Post by bobdob20 on 2008-04-07
I managed to get my X-fi to work using the oss.deb. I might be able to help u get it working. If u got it to install then post the output of 
```
 ossinfo 
```
and see if u get any sound from
```
 osstest 
```

---

