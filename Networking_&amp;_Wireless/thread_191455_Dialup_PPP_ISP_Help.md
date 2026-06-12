---
title: "Dialup PPP ISP Help"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Howiear on 2006-06-07
OK...I've tried the system>administration>networing configuration for my Dialup ISP as well as configuring wvdial and pppon. My system goes through all the steps to dial the isp and when it gets to the ppp handshaking it just sits there.

I'm getting good carrier detect in the plog and it initiates the request but they just won't talk. I had a similer problem with kppp under knoppix 3.7 but when I used pppconfig and pon it worked fine.

I've configure my user information in the pap-secrets and chap-secrets file and followed every online help I could find. I just can't get 6.06 to dialup and connect to my ISP.

I've made sure that I have my ISP dns servers listed in the resolv.cong file as well as going through the settings in both provider files for pon. 

I've seen other posts that the 2.6 kernal may have issues with ppp. Does anyone have any confirmation on this. 

I'm very new to linux and could really use some guidance on how to get this working. 

If I connect through the modem sharing of my WinXP unit I can get the ethernet adapters and even my wireless network adapters to work but I can't get this unit to dial the internet!

---

### Post by johnc4510 on 2006-06-07
I don't know if this will help or not. Back when I had dialup,(early breezy) I had used: gnomeppp for dialup. It was easier to configure and gave me faster download speeds. You might try it to see if this is really a problem with ppp or wvdial. Hope this helps.

---

### Post by zxee on 2006-06-08
Have you used 'pppconfig' from a shell (as root)? Be warned there seem to be significant networking issues with dapper-I don't know why. I would also recomend trying modem monitor. Modem monitor is an applet that you can add to your panel. That is the only gui dial up tool that works on my install of dapper-and it has problems too. Gnome-ppp definately does not work although it worked great in breezy. I also think it would be helpful for dial up users to let the developers know there's a problem. I did file a bug report, but nothing so far on that.

---

### Post by Howiear on 2006-06-14
Yes. I've tried the pppconfig from a shell, root shell and more. I've edited all the appropriate files. Heres what I've found in my searches through multiple online sources.

The 2.6 Kernal has hadd multiple issues with the Microsoft Point to Point Encryption and Microsoft Point to Point Compression (MPPE/MPPC).

[http://mppe-mppc.alphacron.de/](http://mppe-mppc.alphacron.de/) this site gives some insight into these issues. The Kernel that is included in Dapper Drake does have the MPPE module compiled in it but from all I can surmise from my endless search it doesn't have the MPPC modules compiled into it. I haven't found a sourch for these modules and I'm not well versed in the compiling of Kernal myself. 

Bottom line is if your ISP uses microsoft based PPP servers to provide your connectivity you will most likely have issues with any 2.6 kernal of Linux. 

Please! If anyone has more information and if I'm wrong in my assesment post on this thread and correct me. I'm not the most profficient Linux user on the planet and would welcome any and all feedback to this issue.

Thanks, and I hope to see Penguins fly in my lifetime.

---

### Post by zxee on 2006-06-14
That's very interesting Howiear-I'll have to do some reading. I've gotten dial up working on distros like Foresight that don't natively support it, and back in the days of using debian 3.0r1 (woody) I had a huge learning curve to digest with ppp & friends or maybe it's fiends. Anyway to help troubleshoot a system I've found that chestnut-dialer gives a lot of feedback about what's going on and gnome-ppp should do that too but I haven't been so lucky with it plus it appears broken in dapper. Also chestnut-dialer gives you many more options and opportunity to change configuration files. It's just an idea but who knows someone might be helped by the mention of it. Also Howiear, Do you know if there's a list that identifies which isp's are using that protocol?

---

### Post by Howiear on 2006-06-19
Thanks, I'll try the chestnut-dialer, anything is worth a shot. As for which ISP's are using what I have no idea. I do know that most of the ISP's in my little town all run on a Microsoft based system and I would have to assume that they utilize the microsoft compression. I haven't done enough research to prove that out but I do know that's it's the most popular system out there.

I think each ISP would have to tell you what they are using at the time you talked to them about service availability. It's really not a problem at home since my main (Gaming system) is the dreaded XP. I was just hoping to go to a more stable system for my shared dialup networking. I have had shared networking running under a Debian 7 (with the 2.4kernal which supports both MS encryption and Compression) but was hoping to go with the Ubuntu distro. I think the Ubuntu disto is by far my favorite quick no mess distro.

I fear since I'm no lunix guru and don't have time to learn kernel re-compilation I'll have to go back to the Debian 7 distro for now.

Thanks,

---

### Post by hfdragon on 2006-06-20
Where can I find chestnut-dialer, I'll give it a try too... ?

---

### Post by zxee on 2006-06-21
At sourceforge: [http://chestnut-dialer.sourceforge.net/](http://chestnut-dialer.sourceforge.net/)
I have primarily used this in distros like foresight that had no dial up configuration files. I've also used it in slack. I haven't fooled around with chesnut-dialer much in debian based systems although I did install it sucessfully on dapper. I mostly use modem-monitor though because it generally works for me. You may need to adjust/tweak some ppp stuff in debian. Let me know how it goes and if I can be of help.

---

