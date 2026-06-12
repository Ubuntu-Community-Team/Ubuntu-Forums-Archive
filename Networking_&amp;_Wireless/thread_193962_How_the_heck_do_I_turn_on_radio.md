---
title: "How the heck do I turn on radio"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by miceagol on 2006-06-10
After upgrading from Breezy to Dapper it seems my wireless card decided to turn off its radio, but how do I turn it on again? lshw list the card as "*-network DISABLED" and iwconfig has 0 on link, signal etc. [This]("https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide") page tells me to push a key combination on my laptop, but I have no freakin' built-in wireless card. It's in the cardbus. *frustrated* ](*,)

I have a HP Omnibook 6000, and an Asus WL-100g wireless card. Anybody out there with a similar setup? Or is there anybody who knows a simple way to turn on the radio in Ubuntu?

In one week I'm going to Hungary, and I'll be staying there for two months. I'm lost without a working wireless card, and going back to Windows is a BAD, BAD thing. Aaargh! :shock:

---

### Post by VersusGod on 2006-06-10
Hello!

I'm afraid I don't have a solution to your problem, however you were able to solve mine!

I had the exact same problem as you.  Everything was working properly, driver and card identification and everything EXCEPT for the 'Disabled' thin in lshw -C network.  Turns out I inadvertantly disabled my wifi card by hitting a combination of keys on my keyboard. I used it again, and now everything is working again.

Thank you!

-VG

---

### Post by stalefries on 2006-06-10
I would try System>Administration>Networking. Then activate eth0 our wlan0, or whatever is the proper interface.

---

### Post by miceagol on 2006-06-11
[QUOTE=stalefries]I would try System>Administration>Networking. Then activate eth0 our wlan0, or whatever is the proper interface.[/QUOTE]

Nope, doesn't work, tried it. After pushing activate and waiting for a while, it says my card was successfully activated. However that is not true, as the command line still tells me it's disabled, and when I go back into the Networking menu it's deactivated again.

Happy I could help VersusGod. :)

---

### Post by oberon on 2006-06-14
I have the same issue with my bcm4306.  I have a button on the front of the laptop for it, but it doesn't do anything. :confused:   Anyone have any luck using the bcm43xx driver on a Compaq R3000?

---

### Post by miceagol on 2006-06-17
I successfully solved my problems by doing a clean install of Dapper Drake. Details [here]("http://ubuntuforums.org/showthread.php?t=193197&page=2").

---

