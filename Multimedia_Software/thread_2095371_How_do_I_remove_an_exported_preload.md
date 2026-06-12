---
title: "How do I remove an exported preload?"
date: 2012-12-16
forum: Multimedia Software
---

### Post by Labhrain on 2012-12-16
Hello,
I'm pretty new to all this, and I used an LD_PRELOAD command I saw here to make my webcam work with skype.  It worked, so I then did export LD_PRELOAD=yada, yada, yada.  That, did NOT work out well, and causes issues that are even worse than before.  All I want to do now is remove the exported preload so it goes back to how it was before.  Please, if someone could simply give me the commands to do that.  I've been working on all of this for two days and am at my wits end.  Thank you for your help!  I'm using 32-bit ubuntu 12.04.

---

### Post by steeldriver on 2012-12-16
Environment variables don't just persist across reboots - so you must have edited a file somewhere to export the value each time - you need to find which file (possibly your ~/.bashrc file? or a system file like /etc/environment?) and edit it back

---

### Post by Labhrain on 2012-12-16
Thanks.  I actually haven't tried rebooting, so that may very well take care of it.   (Can't believe I didn't try that, as I usually do when all else fails)   If it doesn't work, I'll check on the files.

---

### Post by Labhrain on 2012-12-16
I rebooted, but the issue created after exporting the preload still remains.  I actually thought the idea of exporting a preload was to make it persistent.  That's why I originally did it.  Unfortunately, making it persistent created problems, and that's why I want to get rid of it. 

I've checked the two files you suggested, and there is nothing there indicative of this.

I didn't write to any files directly.  I simply used the following command that I found on another thread here:

"export LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype"  (without the quotes)

I just want to undo whatever that command did.

Thanks.

---

### Post by steeldriver on 2012-12-16
AFAIK that should do no more than set the environment variable LD_PRELOAD to the path specified for the current shell and its subshells

What do you get now if you type

```
echo $LD_PRELOAD
```

---

### Post by Labhrain on 2012-12-16
> **steeldriver said:**
> ells

What do you get now if you type

```
echo $LD_PRELOAD
```

Well, I get nothing.  I mean, it doesn't give me an error.  It simply returns nothing.  So, I guess there's nothing in there, and the new problem is simply an unrelated Skype issue.

I've had a rough go of it with Skype on 12.04.  Every time I start it, it tells me I can't log in due do another instance running.  I've tried every which way to kill the Skype processes, and when all are killed, I start up Skype - same problem.  I think that perhaps double instances are starting when I open up Skype.  It's very, very strange.  I've tried uninstalling (with purge) and reinstalling, but to no avail.  It's really a mess.

---

### Post by steeldriver on 2012-12-16
Hmm... well I don't know what to suggest - I've just installed skype here on my 12.04 laptop and we'll see how that goes

---

### Post by Labhrain on 2012-12-16
> **steeldriver said:**
> Hmm... well I don't know what to suggest - I've just installed skype here on my 12.04 laptop and we'll see how that goes

Hopefully it will go well for you.  I have it installed on my 12.10 64-bit system without any real issues, but I've had problems on the other one.  I have now created a work around shell script to open Skype with the necessary preload using sudo.  When I do that, it opens just fine and the webcam works.  It's a bit clunky, but it does work for now until I find something more elegant.

---

