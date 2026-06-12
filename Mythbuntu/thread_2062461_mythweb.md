---
title: "mythweb"
date: 2012-09-25
forum: Mythbuntu
---

### Post by deanie44 on 2012-09-25
I have Mythbuntu 12.04 installed on an external hd attached to my Windows 7 pc and I can access mythweb.  Unfortunately, when I try to access it from Windows 7 using my wan ip I cannot acess mythweb.  Does Comcast have port 80 blocked?  How can the port be blocked if I can access it from the external hd.  I am confused.  Any assistance will be apprciated.  deanie44

---

### Post by nickrout on 2012-09-25
> **deanie44 said:**
> I have Mythbuntu 12.04 installed on an external hd attached to my Windows 7 pc and I can access mythweb.  Unfortunately, when I try to access it from Windows 7 using my wan ip I cannot acess mythweb.  Does Comcast have port 80 blocked?  How can the port be blocked if I can access it from the external hd.  I am confused.  Any assistance will be apprciated.  deanie44What are you talking about? How can myth be running on an external hard drive while you are running windows?

---

### Post by deanie44 on 2012-09-25
Nickrout.  I have an external harddrive connected to my pc via usb port.  It has mythbuntu 12.04 installed on it.  I am able to record tv shows and use the internet.  That is what I am talking about.  Lets play nice.  I only asked a simple question.  Nevermind I will figure it out.  Why are all the people that understand mythbuntu, ubuntu, etc so mean.  Do not like to share with others.  You have a nice day.  deanie 44

---

### Post by nickrout on 2012-09-25
So how is it running at the same time as the windows machine it is attached to?

---

### Post by Rotak on 2012-09-25
> **deanie44 said:**
> How can the port be blocked if I can access it from the external hd.  I am confused.

I am confused, too. How can you access it "from the external HD"?

Do you have a multi-boot setup? Like booting the PC from the external HD to run Mythbuntu and from internal HD to run Win7?

So Nickrout's question is not mean. It's still unanswered:
[QUOTE=nickrout]How can myth be running on an external hard drive while you are running windows?[/QUOTE]

**So, please explain your system setup.**

Answering your port question is not that simple. If Mythweb is accessible on 127.0.0.1 or a 192.168.?.? address, that doesn't mean you'll also be able to access it from the WAN side.

You need to setup your router to route port 80 to your myth PC IP address. I recommend to change the config to use another port, tho. That would also outsmart your provider, if port 80 is blocked by them.

---

### Post by deanie44 on 2012-09-25
Hi Rotak. I cannot run windows 7 and mythubuntu at the same time. It is on external hd, which is attached to a usb port on my pc. I followed directions I found on the internet. When I want to use mythbuntu, I go into the bios and change the boot order. It is pretty amazing. I will try your suggestion. thank you.  deanie44

---

### Post by deanie44 on 2012-09-25
Sorry Nkckrout.  My apologies.  Keep up the good work!

---

### Post by goffa on 2012-09-25
I think I'm a bit confused as well.

There is a computer, lets call it computer A, with an external HD and can boot to mythbuntu. This runs mythtv backend and from the web browser on this machine you can access mythweb.

Are you saying you have another machine, lets call it computer B if it exists, and you can not access mythweb from this other computer or is there only computer A and when booted to another operating system that does not have mythtv backend running you can not access mythweb?

---

### Post by anonymousdog on 2012-09-25
If you are dual booting, there is no way for Win7 to access mythweb because Mythbuntu would not be running at the time.

---

### Post by nickrout on 2012-09-25
> **anonymousdog said:**
> If you are dual booting, there is no way for Win7 to access mythweb because Mythbuntu would not be running at the time.what he said!

---

### Post by deanie44 on 2012-09-28
Thank you everyone for your responses to my post. It is solved.  Thanks again. deanie44

---

