---
title: "Ubuntu and Windows 7 network problem"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by markoid63 on 2010-11-24
I am running Ubuntu 10.10 on my laptop, and Windows 7 on my Desktop. My laptop is using the wireless network for internet, accesses a printer over the network, and I can see and access public folders on my desktop windows 7 pc. Problem is I cannot see a Ubuntu shared folder on the Windows 7 machine. I have tried to setup a shared folder on the laptop, not sure if I have it right, but am getting frustrated. I have searched many guides and tried to make sure all sorts of settings on both machines are right but I get the feeling I'm missing something. Am a newbie to Ubuntu and Samba, any help would be very appreciated.  :confused:

---

### Post by pawhtiobo on 2010-11-24
I had a similar problem, i solved it by lowering the encryption level of the Windows 7 share (40-56 bit) and disabling password protect sharing:

[IMG]http://www.sevenforums.com/attachments/network-sharing/30815d1255066248-windows-7-network-sharing-2.jpg[/IMG]

Hope that helps :)


See ya...

---

### Post by markoid63 on 2010-11-24
Thanks for the reply, have tried these settings, still no luck. Is it something on my Ubuntu computer I'm doing wrong or is it definately the Windows 7 one?

---

### Post by pawhtiobo on 2010-11-24
Can you ping the Ubuntu machine? if yes...

Can you do in the **run prompt** of Windows 7:

\\youripaddressubuntu\yourshare

See ya...

---

### Post by markoid63 on 2010-11-25
I don't believe it, I got it working. I don't know exactly what I did,  fiddled with a few settings on both machines, rebooted and bingo, there  it is. Thankyou so much for your help, I think you put me on the right  track.   Cheers!   :razz:

---

### Post by pawhtiobo on 2010-11-25
Glad i could help :)

See ya...

---

