---
title: "Custom host files"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by Rytron on 2012-12-01
Hi.

I am using the host file that 'Spybot - Search & Destroy' generated when I tried it in windoze on a course (sadly the only computers were ms).

Can anyone recommend more entries to block or some excellent custom host files?

```
gksu gedit /etc/hosts
```

Some of the entries I have are:
127.0.0.1	[www.007guard.com](www.007guard.com)
127.0.0.1	007guard.com
127.0.0.1	008i.com
127.0.0.1	[www.008i.com](www.008i.com)
127.0.0.1	[www.008k.com](www.008k.com)

---

### Post by vasa1 on 2012-12-01
[http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)
and there's a thread in this forum dedicated to hosts file. Don't use it myself.

---

### Post by Rytron on 2012-12-01
> **vasa1 said:**
> [http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)
and there's a thread in this forum dedicated to hosts file. Don't use it myself.

Nice one. Thanks vasa1.

Is this the thread you were referring to? [http://ubuntuforums.org/showthread.php?t=241460&page=8](http://ubuntuforums.org/showthread.php?t=241460&page=8)

---

### Post by DukeOfMixture on 2012-12-01
[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

You should check it once or twice a month of r updates.

It will eliminate a lot of ads also. When I see posts on YouTube about ads in the comments section I think "What ads?"

---

### Post by vasa1 on 2012-12-01
> **Rytron said:**
> Nice one. Thanks vasa1.

Is this the thread you were referring to? [http://ubuntuforums.org/showthread.php?t=241460&page=8](http://ubuntuforums.org/showthread.php?t=241460&page=8)

Yes, that's the one. It slipped off my radar after being closed!

---

### Post by Rytron on 2012-12-01
> **vasa1 said:**
> Yes, that's the one. It slipped off my radar after being closed!

Great. It is still open.

---

### Post by Rytron on 2012-12-01
> **DukeOfMixture said:**
> [http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

You should check it once or twice a month of r updates.

It will eliminate a lot of ads also. When I see posts on YouTube about ads in the comments section I think "What ads?"

Excellent! Thank you DukeOfMixture.

BTW, would having a very long hosts file slow down opening bookmarks and other links?

---

### Post by DukeOfMixture on 2012-12-01
> **Rytron said:**
> BTW, would having a very long hosts file slow down opening bookmarks and other links?

I think it depends. I had such a problem with Windows, but that was some time ago. I haven't had the problem with Linux.

I have over 16,000 lines in my hosts file from that link and haven't noticed any performance issues.

Best way to see is to test it.

---

### Post by Rytron on 2012-12-01
> **DukeOfMixture said:**
> I think it depends. I had such a problem with Windows, but that was some time ago. I haven't had the problem with Linux.

I have over 16,000 lines in my hosts file from that link and haven't noticed any performance issues.

Best way to see is to test it.

Ok.

Which of these choices is best or is there much difference? Would all work in GNU/Linux?
127.0.0.1    [www.facebook.com](www.facebook.com)
127.0.1.1    [www.facebook.com](www.facebook.com)
0.0.0.0      [www.facebook.com](www.facebook.com)

---

### Post by vasa1 on 2012-12-01
> **Rytron said:**
> Ok.

Which of these choices is best or is there much difference? Would all work in GNU/Linux?
127.0.0.1    [www.facebook.com](www.facebook.com)
127.0.1.1    [www.facebook.com](www.facebook.com)
0.0.0.0      [www.facebook.com](www.facebook.com)

There was an interesting argument in another forum over 127.0.0.1 versus 0.0.0.0  vis-à-vis economy. If I find it I'll post here.

---

### Post by vasa1 on 2012-12-01
Here:
[A tip to cut down the Hosts file]("http://www.wilderssecurity.com/showthread.php?t=321755")

And this:
> 
One additional hint: I use the hosts file from [www.mvps.org](www.mvps.org) but experienced a lot of time-out error messages under WinXP. These time-outs vanished after I replaced all 127.0.0.1 entries with 0.0.0.0 (with the exception of localhost, of course!). Worth a try if somebody experiences the same problem.
Source: [http://www.wilderssecurity.com/showpost.php?p=558518&postcount=4](http://www.wilderssecurity.com/showpost.php?p=558518&postcount=4)

---

### Post by vasa1 on 2012-12-02
You've got me interested in this hosts file business :)
I've dumped Adblock Plus for Chrome since recent versions seem to have some "issues". I moved (back) to Privoxy but the one problem is that Privoxy doesn't do anything about http_s_ sites. The hosts file could come handy in such cases.

While poking around in /etc, I noticed that in addition to hosts, there's hosts.allow and hosts.deny. Wonder what they're all about since whatever I remember reading has been just about the hosts file.

Edit: "hosts.allow and hosts.deny are deprecated."
[http://askubuntu.com/a/23225/25656](http://askubuntu.com/a/23225/25656)

---

