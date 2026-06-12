---
title: "Nero Linux Problem"
date: 2011-10-19
forum: Multimedia Software
---

### Post by cottfcfan on 2011-10-19
In 11.10 whether Ubuntu, Kubuntu or Xubuntu, I'm having the problem of, when I try and add a file to the burn list, I get an "Invalid Argument" error.
It worked fine in all previous versions of Ubuntu.
Anyone else seeing this or know of a workaround?
Thanks.

---

### Post by krishnandu.sarkar on 2011-10-19
What program are you using?? Brasero or what??

Try k3b. It's the best burning program.

---

### Post by cottfcfan on 2011-10-19
Someone hasn't read the title:D
Sorry for the sarcasm. I paid for Nero Linux about a year ago after problems with the native apps. Its worked flawlessly until the latest `buntu's.

---

### Post by wolfen69 on 2011-10-19
> **krishnandu.sarkar said:**
> 
Try k3b. It's the best burning program.

I agree. K3B has all the features of Nero, and has worked perfect for me throughout the years.

---

### Post by cottfcfan on 2011-10-19
I have used k3b today and had a successful burn, and will use it if I have too.
I just prefer Nero (& I paid for it), so I prefer to get that working if at all possible.

---

### Post by mario_k8 on 2011-11-05
> **cottfcfan said:**
> In 11.10 whether Ubuntu, Kubuntu or Xubuntu, I'm having the problem of, when I try and add a file to the burn list, I get an "Invalid Argument" error.
It worked fine in all previous versions of Ubuntu.
Anyone else seeing this or know of a workaround?
Thanks.


Hi, 

I've been experiencing the same problem after upgrading to ubuntu 11.10. I get the exact same error when trying to create an audio cd compilation (data compilations seem to be working fine). I posted this issue on the [nero forum]("http://forum.my.nero.com/index.php?showtopic=10966") and was advised to contact tech support directly. So, I emailed tech support 10 days ago, and their initial response was that they forwarded the issue to the dev team and are waiting for feedback. No news since then. It might be a good idea to report this issue yourself to tech support, because that might help get their attention.

I will let you know if I have any news or find any work around.

Cheers

---

### Post by cottfcfan on 2011-11-05
mario-k8..
Already posted on the Nero forum about a week ago.
Still awaiting a reply.
Will post here when I either get a reply or figure it out.

---

### Post by cottfcfan on 2011-11-12
Just to add to this issue.
Nero Linux works fine in the new Fedora 16.
I can only imagine I need to install some package that's missing.
Still awaiting a reply from Nero.

---

### Post by cottfcfan on 2011-11-15
Can anyone else confirm whether they can burn audio cds with Nero Linux in 11.10, & also is the problem just 64bit or 32bit as well?

---

### Post by cottfcfan on 2011-11-17
OK.
Installed 32 bit Ubuntu & it works fine.
This is purely an Ubuntu 64bit problem.
Any help would be appreciated.

---

### Post by h.aling on 2011-12-03
Same here. Latest nerolinux and same error: "invalid argument".

---

### Post by user666 on 2012-01-15
Same problem here. After i installed "mpg123" it works fine.

---

### Post by cottfcfan on 2012-01-15
user666..
Just installed the package mpg123. The problem still exists, when adding audio files to burn.
Are you using 64bit?
Did you install any other package?
You seem to be the only person who has this working...

---

### Post by user666 on 2012-01-16
Try the following:

create the directory /usr/lib64 (if not exist)
link /usr/lib/nero to the created dir  (ln -s /usr/lib/nero /usr/lib64)

---

### Post by cottfcfan on 2012-01-17
User666, You are indeed a star.
Have had this problem for months. Now it works perfectly.
Thanks again.

---

### Post by beameup on 2013-01-26
User666 Thank You! Was driving me crazy on my 64bit Ubuntu.

---

### Post by ProxyCyber on 2013-01-26
What category are you putting the file under? When I used Nero it did the same, but for example, instead of me doing ISO, I burned to UDF/ISO and it worked. I'm not sure, as I haven't specifically tried on Linux, but that's just a thought -- does it have categories of things you can burn? I probably didn't help, but The user above is more likely to help with the tech support e-mail. Good luck!

---

### Post by beameup on 2013-01-26
Was trying to burn mp3's to audio cd.
I have the 64 bit version too. Thought it might be an issue with the Ubuntu upgrade to 12.1.

---

### Post by wildmanne39 on 2013-01-26
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old.

---

