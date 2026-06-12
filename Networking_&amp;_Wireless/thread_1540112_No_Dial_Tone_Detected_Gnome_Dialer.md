---
title: "No Dial Tone Detected Gnome Dialer"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by zenarcher on 2010-07-27
I'm trying to resolve an issue with a dial up modem and really need some help.  I haven't used dial up in many years and not even sure how to approach the problem.  Making matters worse, I haven't had a landline phone in years, so am trying to troubleshoot this problem and each time have to take it back to a friend, for whom I have installed Kubuntu 10.04.  All works fine on my high speed ethernet and wireless, but I can't get the dial up she needs to work.

The system is a Compaq Presario V2000 laptop.  KInfoCenter reports an ATI Technologies SB400 AC'97 Modem Controller.  I know the modem hardware is fine, as it was working perfectly when I removed Windows XP and installed Kubuntu 10.04.

I tried using KPPP, however KPPP will not let me set the DNS to Automatic...it is grayed out. So, I've installed both wvdialer and Gnome Dialer.  Gnome Dialer seemed to set up fine and all user info. number to dial, etc. was set up.

The problem is that when a telephone line is connected to the modem and you attempt to dial, no dial tone is detected.

I don't know how to approach this, not how to troubleshoot it.  I would be happy to provide any logs or output here, if someone can tell me what to do.

Any help is appreciated!  My friend loves the Kubuntu install, but I have to get this dial up modem working!

Regards,
zenarcher

---

### Post by grahammechanical on 2010-07-27
I used to use a dial-up modem until this spring when I obtained broadband. I would use the command sudo pppconfig to configure the dialer and then type sudo pon in a terminal for the modem to dial the ISP. I do not know if this little program is similar to those you are using. This utility asks for the method of dialing. Should it be Tone or Pulse. The default is set to Tone. Is the telephone handset touch-tone? if so make sure the dialing method is set to tone.

I do not know what else to suggest. I have found that Ubuntu seems set up for always on broadband connections and that dial-up is neglected. I could not get a dialer to work. I would always use a terminal and type sudo pon to dial and sudo poff to disconnect.

Regards

---

### Post by zenarcher on 2010-07-27
Thanks so much for that advice.  I'll give them a try and post back with what I get for a result.  I'd be happy to get this modem working in any manner...even if it requires using the terminal.

Thanks again and I'll post back.  I'll have to find a landline telephone line to give it a try.

Regards,
zenarcher

---

### Post by zenarcher on 2010-07-27
Okay, I am going through the pppconfig from a terminal and when I get to Select Modem Port, none is automatically found.  I only have the option of Manual Selection.  Can anyone tell me how I can figure that out?

Regards,
zenarcher

---

### Post by zenarcher on 2010-07-27
> **grahammechanical said:**
> I used to use a dial-up modem until this spring when I obtained broadband. I would use the command sudo pppconfig to configure the dialer and then type sudo pon in a terminal for the modem to dial the ISP. I do not know if this little program is similar to those you are using. This utility asks for the method of dialing. Should it be Tone or Pulse. The default is set to Tone. Is the telephone handset touch-tone? if so make sure the dialing method is set to tone.

I do not know what else to suggest. I have found that Ubuntu seems set up for always on broadband connections and that dial-up is neglected. I could not get a dialer to work. I would always use a terminal and type sudo pon to dial and sudo poff to disconnect.

Regards

Yes, the handset is touch-tone.  I haven't seen any of the pulse dial phones around in many years here.  I have it set to Tone.

I went through sudo pppconfig.  I was fine until Port detection. pppconfig did not automatically find a port.  I was left with an option for Manual selection.  Looking at the Gnome dialer, the port was automatically detected as /dev/ttySL0.  That was not one of the listed options in pppconfig, but I did change in the manual configuration to /dev/ttySL0.  Then, I finished the rest of the dialer and saved.

The Gnome dialer looks like everything is properly configured.  Even found the port automatically and such, but still does not detect a dial tone.  Any more ideas??

Regards,
zenarcher

---

### Post by zenarcher on 2010-07-28
I don't know if I'm making any progress with this dial up or not.  I followed the instructions for sudo pppconfig and that seemed to be right.  I then entered sudo pon.

When I click on KPPP, I get the screen where I can attempt to connect.  Then, the screen for trying to connect.  I then see..."Looking for Modem," followed by "Modem Ready."  I then get "Initializing Modem," followed by Dialing XXX-XXXX, which would be the telephone number.  Then, the message, "No Dialtone," (That makes sense, since I don't have a phone line connected here.  I have to go try a phone line somewhere with a landline phone.)

As for the Login Script Debug Window....I have the following:

+++ATH

ATZ
OK

ATM1L1
OK

ATDTXXXXXXX (The "X's" would be the number I'm trying to dial.
No Dialtone

I'm not sure if this all looks normal as it should (considering I don't have a phone line connected here).  I'm going to go locate a phone line to connect and see if the modem now sees a dialtone.

I'll reply when I try that.

Regards,
zenarcher

---

### Post by dineshs on 2010-07-29
I am not sure but there is an option in gnome-ppp / kppp dialler with which you can disable``wait for dialtone''

---

### Post by grahammechanical on 2010-07-29
When I used a modem the port I set the port to ttyS0. That is the equivalent to com 1 in DOS. The first serial or com port. Maybe it is a typing error but you have put ttySL0. By the way, for those who don't know,  '0' is a zero, the number 0 not the letter o or O. which you seem to have noticed from what you have typed.

If the landline goes through a switchboard, you may need to insert a number such a 9 before the ISP telephone number. It depends on what number your dial to get an outside line. It is just a thought. 

I have had difficulties like this myself. I became so frustrated that I thought that my wife must surely be pulling out the telephone extension cable that I had run to the room where I was using the computer. I do not mind working things out for myself but I do get frustrated when I cannot solve what should be a reasonably simple problem. You have my sympathy. 

Regards

---

