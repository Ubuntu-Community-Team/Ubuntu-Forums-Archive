---
title: "Bluetooth Can Send Files to Phone, Can't Browse"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by eclipsechasers2 on 2011-10-23
Not sure if this is the correct forum, but it's sort of a networking problem. I can connect my bluetooth-enabled phone to my laptop, and can send files from the laptop to the phone without problem. However, when I try to browse files on the phone (e.g. for uploading pictures), I get the error:

Could not open location 'obex://[B4:B3:62:D9:CE:DB]'
Error while getting peer-to-peer dbus connection: The name :1.104 was not provided by any .service files.

I am able to send and receive files from Windows. If it matters, phone is an AT&T Go Phone

---

### Post by eclipsechasers2 on 2011-10-23
Smileys in above message are colon followed by D. Not sure how to turn off this automatic "translation" in this forum.

---

### Post by jameskinds on 2011-11-11
Hi,

I am having *exactly* the same issue. I can send files via bluetooth to the phone, but I get the same error message if I try and browse files on the phone.

I am running a fully up to date Ubuntu 11.10 with an Asus USB dongle.

Does anyone have any clues?

Thanks,

James

---

### Post by aranad on 2011-11-17
I've been getting this exact same thing too. It's really annoying because its the only way I can get photos off my phone. It was working perfectly until I upgraded to Oneiric :-(

---

### Post by ernstlenzer1 on 2012-02-01
*bump* Does anyone have a solution for this yet?

---

### Post by charlescarroll1 on 2012-02-15
I've been trying to figure this out as well. I click on "Browse Files" in the Bluetooth manager and nothing happens. I noticed that my phone appeared in the file manager, but when I click on it I get the same message

> Could not display "obex://[C8:AA:21:A9:08:FA]/".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

Does anybody know how to fix this?

---

### Post by SeijiSensei on 2012-02-15
Most phones require a PIN number to authorize access to the hard drive.  The two Bluetooth phones I've owned, one from LG and one from Samsung, use "0000" as the PIN by default.  In Kubuntu 11.10, you'll get prompted for the PIN when making an OBEX connection.  You may need to enter the PIN on the phone as well.

---

### Post by dixoncx on 2012-03-12
Me too was facing the same problem...
But now i found a fix..:-)

[http://www.worldofnubcraft.com/1767/a-bluetooth-quick-fix-hack-for-ubuntu-11-10/](http://www.worldofnubcraft.com/1767/a-bluetooth-quick-fix-hack-for-ubuntu-11-10/)

It works fine for me...:)

---

### Post by Chip88 on 2012-03-17
Hey together!

Just the day before yesterday I installed a fresh version of **Kubuntu 11.10** on my new **Lenovo Z370**. Concerning the bluetooth, I can send files from my **smartphone (Sony Ericsson, Xperia Arc S)** without any problems.

But it's impossible for me, to send files from my notebook to my smartphone. I nor can't browse my smartphone through Dolphin. Trying to open via *bluetooth://[MAC - address of my phone]/* , the option "Send files" appears and I can choose a file, but the sending fails always!!!

The command *hcitool scan* lists my phone with the correct MAC - address.

I used already Google to find for a solution and I even found some fixes, but neither [http://ubuntu.igameilive.com/2011/11…th-fix-in.html](http://ubuntu.igameilive.com/2011/11…th-fix-in.html) nor [http://ubuntu-answers.blogspot.de/20…untu-1110.html](http://ubuntu-answers.blogspot.de/20…untu-1110.html) didn't work with me at all!!! :mad:

I tried to install *blueman*, but he doesn't open the programme after installation (even not from the console!).

In the configuration of bluetooth on my smartphone, it says always: "Paired, but not connected".

I'm really desperate and I don't have any idea how to fix this... :confused:

For your help, I am very grateful to you in advance!

Best regards from Germany (and sorry for my bad English! :KS)

Chipy

---

### Post by Chip88 on 2012-03-19
Hey guys!

Thanks to an adive in the German Ubuntu Forum, I could solve my problem and just wanted to let you all know. Maybe there is someone who has the problem. So following my instruction, it is possible to fix the problem mentioned above.

Add in the file */etc/rc.local* between the comments and *exit 0* just the code: ```
hciconfig hci0 sspmode 0
```

After restart your notebook, you can send files from your notebook to your cellphone without any problems.

Best regards,
Chipy

---

### Post by eclipsechasers2 on 2012-05-27
Chipy,

Thanks! Adding the line you suggested to /etc/rc.local got my bluetooth connection working.

---

