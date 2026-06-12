---
title: "Internet connection problem"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by Stijn.heirstrate on 2010-11-04
Hello

I'm a Linux noob and I have just installed Ubuntu 10.10 on my laptop, the problem is that there is some sort of internet problem
I select my internet box and type my password, it try's to connect for a minute but it keeps getting back the box with the internet box and password, I swear to god my password must be right cause I tripple checked and typed it, does anybody know what might be the problem?
I appreaciate the help.

-Stijn

---

### Post by cracker89 on 2010-11-04
internet box? kindly elucidate. Do you mean passphrase? WEP? is it wifi? wired? etc. 

I think you need to see this >>>  [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Stijn.heirstrate on 2010-11-04
The wireless Network authentication is required to connect to the internet

I select WPA & WPA2 personal (it's pretty much the only choice there is) for wireless securaty

and my password in the password thing.
I click connect, I see the icon in the right corner moving for a min, it seems it's trying to connect, but it suddenly stops and the wireless Network authentication box appears again, my password still typed. I click "connect" again and I get the same thing again a min later.
Sorry if I'm being unclear.

-Stijn

---

### Post by cracker89 on 2010-11-05
[FONT=Fixedsys]Right. So its a wireless connection. Confirm what type of security option is used by your router and the authentication type. 
If it is correct and as you are using it, and if the password is correct, maybe you need to update?
post output of ```
lspci -v
``` meanwhile?[/FONT]

---

### Post by dineshs on 2010-11-05
See if these links can help
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)
[http://ubuntuforums.org/showpost.php?p=9767936&postcount=11](http://ubuntuforums.org/showpost.php?p=9767936&postcount=11)

---

### Post by grahammechanical on 2010-11-05
What password are you using? The login password? I have made that mistake in the past. What you need is the WPA-PSK key, also called the wireless key. You might find it printed on a label stuck on the bottom of the modem. 

Regards.

---

### Post by cracker89 on 2010-11-06
One more thing, what kind of a network is it? do you have access to the router, or is it a public wifi of somekind?

---

