---
title: "Running Hydrogen and qjackctl as root"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-04-12
I just installed Hydrogen and found I need to run both it and qjackctl as root to get realtime access. Hydrogen changes speed and crackles without Jack's RT parameter set. Right now I'm opening both with "gksu". I can run Ardour in RT without starting qjackctl or Ardour as root. 

How can I get Hydrogen working without running as root?

---

### Post by Patrick K on 2007-04-13
bump

---

### Post by Patrick K on 2007-04-14
Since I'm not getting any answers, I have another question. 

How risky is it running Jack and Hydrogen as root?

---

### Post by Patrick K on 2007-04-27
Bump

---

### Post by jondecker76 on 2007-04-27
I am by no means an expert on the subject and have limited experience thus far, but have done a lot of reading on the subject...

From what I have read, giving applications root access is a no-no security wise. However, i have found relatively few horror stories on the subject. 

What you really need is a real-time kernel. The standard Ubuntu kernel is not a real-time kernel. There is a low-latency kernel in the repos that is better than the stock kernel, but this isn't real-time either.

Now with all of that being said - Ubuntu Studio is very close to release. They are working on a real-time kernel. My recommendation is to wait it out - i believe it will be well worth it once Ubuntu Studio is released along with their real-time kernel

Hope this helps

---

### Post by Patrick K on 2007-04-27
I've been keeping an eye out for Studio. It seems to keep getting pushed back. Hopefully, it will come out soon. Thanks.

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by Patrick K on 2007-05-02
bump

---

