---
title: "Can I force Mythweb not to use WAP"
date: 2008-09-10
forum: Mythbuntu
---

### Post by volkswagner on 2008-09-10
I have a flash enabled cell phone.  Even if I try to force mythweb to reset template it still uses wap.

```
http://mydomain.com/mythweb/'?RESET_TMPL=true'
```

I tried the above on my N95 via Nokia browser and Opera mini.  It still uses the WAP settings.  

Can I watch media on my phone?

---

### Post by managementboy on 2008-09-10
> **volkswagner said:**
> I have a flash enabled cell phone.  Even if I try to force mythweb to reset template it still uses wap.

```
http://mydomain.com/mythweb/'?RESET_TMPL=true'
```

I tried the above on my N95 via Nokia browser and Opera mini.  It still uses the WAP settings.  

Can I watch media on my phone?

I guess there are two ways of doing this, either change the referer settings on your phone (if even possible) to something like firefox or check the 

mythweb/includes/mobile.php

file, that contains all the mobile phones

---

### Post by volkswagner on 2008-09-10
Thanks for the reply.  I can't find the file you listed.

```
find: mobile.php: No such file or directory
```

EDIT:  I found it.  I was using the wrong syntax, to find in any directory.

---

### Post by volkswagner on 2008-09-10
Not sure if this helps.

From apache access.log, using phone from outside network wap.

```
12.168.xx.xx - - [10/Sep/2008:20:41:56 -0400] "GET /mythweb/'?RESET_TMPL=true' HTTP/1.1" 401 504 "-" "Mozilla/5.0 (SymbianOS/9.2; U; Series60/3.1 NokiaN95_8GB-3/1.2.011 Profile/MIDP-2.0 Configuration/CLDC-1.1 ) AppleWebKit/413 (KHTML, like Gecko) Safari/413"
```

I get the same on local network.

Attached mobile.php, if anyone can suggest how/what to edit.  I am open to global WAP off if need be.

---

### Post by volkswagner on 2008-09-14
Even if I could get mythweb to display the non wap interface, playing flash vids on the N95 is far off.

[http://www.gossamer-threads.com/lists/mythtv/users/337645]("http://www.gossamer-threads.com/lists/mythtv/users/337645")

:(

---

### Post by Nikas on 2008-09-14
Do you need the ' ?

Try with [http://mydomain.com/mythweb/?RESET_TMPL=true](http://mydomain.com/mythweb/?RESET_TMPL=true)

---

### Post by volkswagner on 2008-09-15
Thanks for the suggestion.  I get a page that says

"An unknown module was specified"

Do you know how I can disable WAP?

---

### Post by ufgrat on 2009-03-07
It's an old post, but since I found it while looking for the answer (and it put me on the right track), I figured I should contribute.

In the file 'includes/mobile.php', force the function 'isMobileUser' to return a false value:

```
function isMobileUser() {
  return false;
#  return (getScreenSize() === false) ? false : true;
}

```
Note... this COMPLETELY disables WAP support.  No, really.  Your mythweb installation will never, ever, ever recognize a device as needing WAP.

Hope that helps someone...

---

### Post by volkswagner on 2009-07-01
> **ufgrat said:**
> It's an old post, but since I found it while looking for the answer (and it put me on the right track), I figured I should contribute.

In the file 'includes/mobile.php', force the function 'isMobileUser' to return a false value:

```
function isMobileUser() {
  return false;
#  return (getScreenSize() === false) ? false : true;
}

```
Note... this COMPLETELY disables WAP support.  No, really.  Your mythweb installation will never, ever, ever recognize a device as needing WAP.

Hope that helps someone...


Thanks, It sure helped me!

---

### Post by molder on 2009-07-08
My MythWeb is stuck in WAP mode.  [http://ubuntuforums.org/showthread.php?t=919440](http://ubuntuforums.org/showthread.php?t=919440)

I changed /usr/share/mythtv/mythweb/includes/mobile.php per [http://ubuntuforums.org/showthread.php?t=919440](http://ubuntuforums.org/showthread.php?t=919440)  

I preferred the original better.  

I tried following the instructions in reverse but [COLOR=Black]now [/COLOR]everything still gets the WAP treatment.  I added the suggested above line of code > function isMobileUser() {
  return false;
#  return (getScreenSize() === false) ? false : true;
}

Still getting WAPed in Firefox.

---

### Post by tgm4883 on 2009-07-08
> **molder said:**
> My MythWeb is stuck in WAP mode.  [http://ubuntuforums.org/showthread.php?t=919440](http://ubuntuforums.org/showthread.php?t=919440)

I changed /usr/share/mythtv/mythweb/includes/mobile.php per [http://ubuntuforums.org/showthread.php?t=919440  ]("http://ubuntuforums.org/showthread.php?t=919440")  

I preferred the original better.

I tried following the instructions in reverse but [COLOR=Black]now [/COLOR]everything still gets the WAP treatment.

By adding '?RESET_TMPL=true' to the end of the url it should clear up your issue

---

### Post by molder on 2009-07-09
I visted [http://xxx.xxx.x.xxx/mythweb?RESET_TMPL=true](http://xxx.xxx.x.xxx/mythweb?RESET_TMPL=true) and it fixed my problem.  Thanks.

---

