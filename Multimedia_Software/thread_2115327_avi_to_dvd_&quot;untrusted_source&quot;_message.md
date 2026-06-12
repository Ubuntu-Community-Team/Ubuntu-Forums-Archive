---
title: "avi to dvd &quot;untrusted source&quot; message"
date: 2013-02-12
forum: Multimedia Software
---

### Post by Barney-R on 2013-02-12
This is probably my fault for sticking with a version of Ubuntu (10.10) that's no longer supported, but I'm trying to burn an .avi file to DVD in normal DVD format (UK in case it's relevant).

I've tried Brasero, which tells me in needs dvdauthor, which it then refuses to load because it's from an untrusted source.

I've tried DeVeDe, but that won't install either for the same reason.

Whatever I try, I get the same "untrusted source" message, and that's as far as I get.

I've tried installing from the Software Centre, and also from the terminal. Could it be that the relevant files are no longer available for 10.10, or am I doing something wrong?

---

### Post by ibjsb4 on 2013-02-12
I think you have answered your own question.  You need an up to date version and not 10.10.

But guess you could try with 10.10.   This link is dated but looks like it should still work.  I have not tried this myself so you may want to wait for some other replies.

[https://help.ubuntu.com/community/EOLUpgrades#Requirements](https://help.ubuntu.com/community/EOLUpgrades#Requirements)

---

### Post by Barney-R on 2013-02-12
Thanks for the suggestion, ibjsb4. Unfortunately the terminal didn't understand the commands, so it looks as if we'll have to wait for someone else. Either that or do what I should have done some time ago and upgrade to 12.04.

---

### Post by Barney-R on 2013-02-13
Update.

Could it be that the repositories for 10.10 have been removed?

Whatever I try, I keep getting roughly the same message, that the software I want comes from an "untrusted source" and that's as far as I get.

If I try installing from the terminal, I get a 404 (not found) message.

I've only tried to install software related to this particular problem (avi to dvd), so don't know whether it would apply to anything else I might want to install.

I even downloaded the DeVeDe setup file and tried to install it that way, but again it refused, saying (as I understood it) that something was missing from the package. I wasn't even allowed to extract the .tar file.

---

### Post by Barney-R on 2013-02-13
More info.

Looks as if I'm on my own here, but I'll keep trying.

I tried (again) typing "sudo apt-get install dvdauthor" (without quotes) into the terminal. It started, and then gave a message about "unauthorised sources" (or something like that), and asked whether I wanted to continue. I answered "y", and this is the last part (just the error message) of what appeared in the terminal window.

Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe dvdauthor amd64 0.6.18-1build1
  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/d/dvdauthor/dvdauthor_0.6.18-1build1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/d/dvdauthor/dvdauthor_0.6.18-1build1_amd64.deb)  404  Not Found [IP: 194.169.254.10 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I don't know how to use "--fix-missing". Would it help in the case of a 404 error? If so, could someone please explain what I need to type into the terminal to apply the fix?

Someone? Anyone?

---

### Post by bantuvez on 2013-02-13
Download a suitable .deb file from [here]("http://gb.archive.ubuntu.com/ubuntu/pool/universe/d/dvdauthor/"), and try installing it.

---

### Post by Barney-R on 2013-02-13
Thank you bantuvez. That worked (apparently). I was able to install it, so now I'll test it.

I'll let you know if it works (or not), and then HOPE to be able to mark this thread as solved.

---

### Post by Barney-R on 2013-02-13
Thanks again for your help, ibjsb4 and bantuvez.

The dvdauthor installed properly, but I'm still having issues with needed downloads failing with an "untrusted source" message, so I think it's time to cut my losses and install a later version of Ubuntu.

Obviously the download repositories are no longer available for 10.10, which I suppose is understandable.

I'll mark the thread as solved.

---

### Post by col48 on 2013-02-13
Heck, I know nothing, but would the bits you need be in the still (for a little while) supported 10.04 repositories?

---

