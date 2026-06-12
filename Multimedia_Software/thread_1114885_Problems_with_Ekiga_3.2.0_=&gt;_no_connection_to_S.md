---
title: "Problems with Ekiga 3.2.0 =&gt; no connection to SIP"
date: 2009-04-03
forum: Multimedia Software
---

### Post by seppl82 on 2009-04-03
Hi all,

since the update to Version 3 (shipped with Jaunty) i'm not longer able to connect to my sip provider (1und1) in my case.

I'd like to ask you if you have similar problems. => If yes Please tell me then i'll open a Bug in Launchpad.

For my Detailed Problems see here
[https://answers.launchpad.net/ubuntu...question/66072](https://answers.launchpad.net/ubuntu...question/66072)

Thanks
/Seppl

---

### Post by tagbre on 2009-04-26
I'm having this problem too. Fresh install of Ubuntu Jaunty and newly created ekiga.net account. It doesn't work, I always get the message: could not register sip.

---

### Post by Canaryguy on 2009-04-30
Hi,
I'm using Ubuntu 9.04 x64 on a laptop and I had the same problem with Ekiga 3.2.0. I got the message "Could not register SIP:...."
What I did and worked was to open Ekiga and then Edit>Configuration Assistant
When asked for your user name and password enter them as you received them in your e-mail address when you registered in Ekiga.
In the Windows Ekiga Call Out Account I checked the "I do not want to sign up......" at the bottom.
In "Connection Type" you choose your best option. I chose DSL/Cable 512...
In the "Audio Devices" I chose HDA/INTEL (PTLIB/ALSA) in the three boxes. And I think it was this option that made my Ekiga to work fine. Maybe you have to try different audio settings until you see that the Echo Test icon turns green and you can make a call.

It seems I have to repeat this process every time I open Ekiga.

I'm sorry I cannot be more helpful.

Bye.

---

### Post by amendt on 2009-04-30
Yes, I always get "Segmentation fault" error also.  I am using link2voip as my sip provider. I wonder if it has to due with [this]("https://bugs.launchpad.net/ekiga/+bug/362804") bug.

---

### Post by mlkovacs on 2009-05-06
Same problem here. In my case I upgraded to Jaunty from Intrepid. I could call out from voip.ms sip provider but not receive any calls. Back to running Zoiper till this is fixed.

---

### Post by psychok7 on 2009-05-19
same thing here.. i cant even send messages, nor ear any sound.. any way to fix it?

---

### Post by guyguyguy on 2009-11-13
I had similar problems on karmic 64 bit on a Lenovo T400.
At the end, linphone and twinkle worked best for me (and linphone has video)
Gizmo had sound problems and ekiga had the problems you mentioned above.
Here's how I ended up configuring this in ubuntu karmic 64
1. Install linphone or twinkle
2. add a new account, 
   A. for gizmo : 
       set your username as  
                 sip:[gizmo_account]@proxy01.sipphone.com
and your proxy as  
                  sip:proxy01.sipphone.com
  B. For ekiga replace proxy01.sipphone.com with ekiga.net


hope it helps
guy

---

### Post by amp3030 on 2010-01-13
Same problem with karmic 32bit and Ekiga 3.2.5 installed from repository.

---

### Post by afrodeity on 2010-03-24
could not connect to remote host

could not register (transport error)

could not unregister (transport error)

---

### Post by YannickDefais on 2010-04-05
Hi,

Please give this special version a try:
[https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa)

Best regards,
Yannick

---

### Post by tanas on 2010-04-16
> **YannickDefais said:**
> Hi,

Please give this special version a try:
[https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa)


That version did it for me!!
 (There was not sound being sent and it was consuming all CPU - I am using SIP)
Thanks!

---

### Post by green69 on 2010-06-09
> **YannickDefais said:**
> Hi,

Please give this special version a try:
[https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa)

Best regards,
Yannick

I'm using ubuntu 10.04 and this thread didn't solve for me.

---

