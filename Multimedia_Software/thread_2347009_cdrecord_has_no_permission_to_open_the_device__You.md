---
title: "cdrecord has no permission to open the device  You may use K3bbsetup to solve..."
date: 2016-12-20
forum: Multimedia Software
---

### Post by happydog500 on 2016-12-20
I like k3b for buring CD's. When I tried to burn one today, It will go all the way to 99%, then I get these errors;

 > cdrecord has no permission to open the device 
You may use K3bbsetup to solve tis problem. 

 Out of all the installs I've had over the years, I've never had this problem before. I went into k3b setup, I can see three places to "change" the Rom drive. 

 Why am I getting this, and what can I do to fix it?

 Thank you,
 Chris.

---

### Post by Yellow Pasque on 2016-12-20
You can change this in k3b's Settings -> Setup System Permissions menu
Check "use burning group" and change 'burning' to 'cdrom'. Then check cdrecord (which should list the path as /usr/bin/wodim) and click Apply.

Or if you would prefer a simpler copy/paste command to run in terminal:
```
sudo chown root:cdrom /usr/bin/wodim
```

---

### Post by Yellow Pasque on 2016-12-20
Oh, and haven't I seen you somewhere before? ):P
[http://www.linuxquestions.org/questions/linux-software-2/what-about-the-new-amd-drivers-i-keep-hearing-about-4175593359/](http://www.linuxquestions.org/questions/linux-software-2/what-about-the-new-amd-drivers-i-keep-hearing-about-4175593359/)

---

### Post by happydog500 on 2016-12-21
> **Temüjin said:**
> ...Or if you would prefer a simpler copy/paste command to run in terminal:
```
sudo chown root:cdrom /usr/bin/wodim
```

Nice, that was quick!! 

  Thank you,
 Chris.

P.S. Do you have a command as easy as that to make a monitor stay default?

---

### Post by Yellow Pasque on 2016-12-24
> **happydog500 said:**
> P.S. Do you have a command as easy as that to make a monitor stay default?

Not off the top of my head (I don't do multi-monitor). I suggest you create a new thread, and give more info like your GPU/driver and what desktop environment you're using.
Also, please mark this thread solved (thread tools menu above the initial post).

---

