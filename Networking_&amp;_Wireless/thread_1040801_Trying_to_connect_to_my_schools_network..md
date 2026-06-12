---
title: "Trying to connect to my schools network."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by bedake on 2009-01-15
Hello, I am trying to connect to my schools network on my HP dv1000 laptop with its broadcom 4318 card.  The school uses WPA Radius with TKIP key exchange encryption and PEAP and MSCHAPv2 authentication.

I configure network manager to those settings and enter in my username and password but network manager fails to establish a connection.  Would anyone be able to kindly provide advice as to what I might be doing wrong or why its failing to connect?

---

### Post by phantom3113 on 2009-01-15
Do you know if your school has a file or something you have to download and run? At my university, the first time you connect, you have to download their "Bradford_dissolvable_agent". It's just a quick prompt that gives your computer a quick runthrough to make sure you're alright to connect, and then it vanishes or whatever and lets you on. (on windows, it shows up as a ".exe". On ubuntu it should be a ".sh" or shell script)

If this *is* the case, download the file and then enter the following into a terminal:

*note(s): do not enter things in brackets or quotes
```
cd "Directory where .sh file lies, most likely Desktop"

chmod u+x "filename".sh [this makes it executable]

"filename".sh [this runs it. it'll take care of the rest]
```

Hope this helps. Also, you may have to precede chmod with "sudo".

---

### Post by bedake on 2009-01-17
> **phantom3113 said:**
> Do you know if your school has a file or something you have to download and run? At my university, the first time you connect, you have to download their "Bradford_dissolvable_agent". It's just a quick prompt that gives your computer a quick runthrough to make sure you're alright to connect, and then it vanishes or whatever and lets you on. (on windows, it shows up as a ".exe". On ubuntu it should be a ".sh" or shell script)

If this *is* the case, download the file and then enter the following into a terminal:

*note(s): do not enter things in brackets or quotes
```
cd "Directory where .sh file lies, most likely Desktop"

chmod u+x "filename".sh [this makes it executable]

"filename".sh [this runs it. it'll take care of the rest]
```

Hope this helps. Also, you may have to precede chmod with "sudo".



Thank you for your response,  The school does provide a security certificate, I downloaded it and loaded the file with networkmanager but it did not help me to connect succesfully.  Are you referring to a script?  There is nothing like that available I am aware of.

Here is the schools wireless web page: [http://8help.osu.edu/2672.html](http://8help.osu.edu/2672.html)

 perhaps it has some information I am failing to recognize.

---

### Post by literatedegenerate on 2009-01-17
I just resolved a similar situation trying to connect to my schools network. It turns out that driver for my ralink rt2700e wireless card did not support WPA encryption. After searching forums and talking to IT guys I finally found I simply needed to uninstall the driver on my machine and install the windows driver for my card with ndiswrapper.

---

### Post by phantom3113 on 2009-01-18
Yeah, those commands referred to a script. At least your school mentions Linux! All the IT help pages refer to windows only, so I was all on my own with my experience. :P Unfortunately, I haven't had any experience with the kind of security your school is using, so I probably can't be too much more help, but I'll try. In Network Manager, I assume you have the security settings for your school's connection set to either Dynamic WEP or WPA & WPA2 Enterprise, which would give you all the options for a user certificate and such. I would suggest trying what literatedegenerate suggested and seeing if that works. Sorry for the limited assistance!

---

### Post by bedake on 2009-03-30
I've still been unable to connect to my schools network, ndiswrapper seems to be no help either.  It's unfortunate to say this but I believe im going to have to repartition my hdd for windows, this headache is getting old. :(

Just out of curiosity, does anyone with a broadcom 4318 card connect to a wireless network such as this know anything about why mine might not be connecting?

---

### Post by blackstripes on 2009-04-01
> **bedake said:**
> I've still been unable to connect to my schools network, ndiswrapper seems to be no help either.  It's unfortunate to say this but I believe im going to have to repartition my hdd for windows, this headache is getting old. :(

Just out of curiosity, does anyone with a broadcom 4318 card connect to a wireless network such as this know anything about why mine might not be connecting?

I've got the same problem with my school and TKIP.  I have an HP Mini with a broadcom 4312 card...

---

