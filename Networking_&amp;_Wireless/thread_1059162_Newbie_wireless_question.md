---
title: "Newbie wireless question"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by bingo1978 on 2009-02-03
I have been using Ubuntu/Linux variants for about two and a half years and I love it. I am sorry I have to ask this, but here goes. In XP it would show all the available wireless connections. Is there a way to set this up in Ubuntu? My wireless works, but only with my router. I am using a wired connection right now because I have to turn off the encryption on my router to make it work. I am using a broadcom internal modem in a Dell Inspiron B120 if that helps. I am sure it is something I have overlooked. I did search and I found nothing that explained this. Thanks in advance.

---

### Post by nixscripter on 2009-02-03
If you have your GUI set up the default way, there should be a networking icon in the "task bar" -- northeast corner of your screen. If the wireless card is on, pull it down to list all available networks.

---

### Post by bingo1978 on 2009-02-03
That's just it. I pull it down and I only see mine. I know there are at least 3 others very close. XP picks up at least that many. Is the range of my wireless affected by Ubuntu? It is 8.04 if it matters.

---

### Post by nixscripter on 2009-02-03
The radio might be set to a lower transmitter power, or the software might have a lower sensitivity threshold.

If you look at the [iwconfig man page]("http://linux.die.net/man/8/iwconfig"), you may be able to adjust the **sens** and **txpower** attribues (if your card supports it). Some do, some don't.

---

### Post by bingo1978 on 2009-02-03
It says operation not permitted. Thanks for the suggestion. Any other options?

---

### Post by Ayuthia on 2009-02-04
What version is your card (lspci -nn)?  You might be able to use a different wireless module for your card.  I am thinking that the b43 module in the Intrepid kernel has some improvements in the signal strength but I cannot remember how well it was in Hardy.

---

### Post by bingo1978 on 2009-02-04
When I type lspci in the terminal I get the following. It might as well be in Farsi.

---

### Post by Ayuthia on 2009-02-04
The other option that might improve your signal would be to use ndiswrapper.  Here are two links that might help you install it:
[http://ubuntuforums.org/showthread.php?t=1047710](http://ubuntuforums.org/showthread.php?t=1047710)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by bingo1978 on 2009-02-04
I checked out both links. I downloaded and installed the broadcom firmware again. I am still only showing my wireless network. I am showing six with XP. I can provide any info you need, but you might need to keep the terminology simple. I am still learning. Thanks for the help thus far.

---

### Post by TRH1 on 2009-05-24
Just installed Ubuntu 9.04 along with windows vista on a satellite laptop.  I can not turn on the wireless device in Ubuntu, it work fine in windows.  I am new beginner with linux.

---

