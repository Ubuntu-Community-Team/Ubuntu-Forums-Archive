---
title: "Ceton infinitv USB tuner woes with Mythbuntu 12.04"
date: 2012-10-02
forum: Mythbuntu
---

### Post by Bert Berlin on 2012-10-02
I have a Ceton USB infinitv box, with a cable card installed.  It works fine on the Windows Media center, but, for various reasons,I want to switch to Mythbuntu

So, i installed a second internal AV-type of hard disk, and put Mythbuntu 12.04.+ on it, and installed the updates up through today.

After a brief discussion with Ceton support, i was able to compile their usb user-space driver, and install it. 

However there are a couple of problems - not the least of which is that the Ceton tuner is not visible to the backend.  It does have an ip address, of 192.168.180.3, but apparently the backend cannot connect to it.

Has anyone successfully accomplished this setup?  The Ceton support person emailed saying that he though there was a problem in 0.25. Here is a direct quote from the support person, taken from his email:

"I do want to note though that myth 0.25 had issues playing video off
our USB tuner last time I checked. It seemed to be an issue in myth
that I didn't have time to look into."

Anyone able to help with this?

thanks
Bert

---

### Post by Akriss on 2012-10-02
If I remember right. Support for the USB Ceton tuner did not make it in to .25 

However .26 does have it. According to [[COLOR="Red"]This Web Page.[/COLOR]]("http://code.mythtv.org/trac/ticket/10952")

---

### Post by Bert Berlin on 2012-10-02
Excellent news.  Thank you for the information and the link.  I am anxious to test this.

Any idea when the .26 release is due out?

Bert

---

### Post by hackmeister on 2012-10-03
> **Bert Berlin said:**
> 
Any idea when the .26 release is due out?


0.26 is officially out today. No idea when the final packages will make it into the mythbuntu repos. Maybe a day?

---

### Post by Bert Berlin on 2012-10-03
I successfully compiled 0.26 from source, and did the make install. Now, however, when i attempt to start the mythtv-setup, i get an error that says that the backend server uses protocol 72, and the front end uses protocol 75.  How do i fix that?

thanks
bert

---

### Post by Bert Berlin on 2012-10-03
I restarted the backend mythtv, and the message about protocols disappeared, and the mythtv-setup started ok.

From there I was able to attempt to configure the Ceton Infinitv usb box, using its correct ip.

However, a probe of the box fails, as does an attempt to connect to it.

So - got a little further, but am not there yet with 0.26.

Also, now the front-end will not start.

bert

---

