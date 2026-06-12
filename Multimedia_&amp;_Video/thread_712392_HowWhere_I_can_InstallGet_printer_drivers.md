---
title: "How\Where I can Install\Get printer drivers?"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by Turge on 2008-03-01
Hello.
I have brother printer a new one I have bought today.
the name brother MFC-465CN and I get the drivers from they website.
I get the driver for windows xp.
they have there to choose the download for mac or windows so I have choose for windows, and I don't know how to install it, or there is special drivers for ubuntu linux?
[B]
so can somebody help me how I install those driver or get new driver for ubuntu linux?[/B]

thank you.

---

### Post by linuxwizard on 2008-03-01
Get the driver you need here > [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) > Drivers for Debian

Install Howto
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)

---

### Post by TomBull on 2008-03-01
Depends on what you are looking for.
Turbo Print has drivers intended for commercial use. They are not free.
I have a Canon iP4000 and some of the features my printer has do not work with linux drivers.
With Turbo Print they do.
I didn't mind paying for something if it works better, but free is good.

---

### Post by Turge on 2008-03-02
Now only the printer works, the scanner and fax do not work.
and the fax when I put the cable into the printer it's ringing.
I don't know why.

somebody can help me with install the fax and scan?

---

### Post by Turge on 2008-03-02
Any Answer?

---

### Post by linuxwizard on 2008-03-02
All you had to do is look at the bottom of the page the link I gave in my first post > [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) > [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html) > [http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html](http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html)

---

### Post by is511 on 2008-03-02
linuxwizard, can you please break this down for a complete noob?  I have two days of experience with Linux.  :-)

I have the pages listing the Brother drivers, but the instructions (and FAQ) seem to be written somewhat for someone who's at least somewhat familiar with Linux already.  My questions:

Do I download the package installer and run it or do I have to download it, then enter commands at the command line to run it? 

Is there a certain file that I should download the package to or does it matter? 

In what order do I type the commands?

Please help! Thank you!

---

### Post by Turge on 2008-03-03
> **linuxwizard said:**
> All you had to do is look at the bottom of the page the link I gave in my first post > [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) > [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html) > [http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html](http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html)

men the tutorials u gave me works but, i try to install scanner and everything i install good, and than the scanner works only in root and i make the tutorial in "su"command, not in root.
like it's say here :
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html")

when i go to applications -->graphics -->Xsane image scanner
[B]
then it's search and give me that error :
"Failed to open device 'brother2:bus5;dev1':Error during device I/O.
But in root it's work's so why it's like that?

And in the fax i have that probleam :
when i put the cable in to the printer so it's only rings all the time and i can't stop it, maybe u know what the probleam can be? [/B]

---

### Post by Turge on 2008-03-03
Any answer?

---

### Post by linuxwizard on 2008-03-03
From here > [http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#20](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#20) > The current version of Brother Linux scanner driver works only with a root user. To use it with a normal user, you need to make the settings which depend on your distribution.  Good Luck

Not for sure if this is your issue with Fax > [http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html](http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html) >  Do not use our PC-FAX Driver in USA.
Our PC-FAX drivers do not suit the USA Telecommunication Regulations. Good Luck

---

### Post by Turge on 2008-03-04
> **linuxwizard said:**
> From here > [http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#20](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#20) > The current version of Brother Linux scanner driver works only with a root user. To use it with a normal user, you need to make the settings which depend on your distribution.  Good Luck

Not for sure if this is your issue with Fax > [http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html](http://solutions.brother.com/linux/sol/printer/linux/pcfax_drivers_lpr.html) >  Do not use our PC-FAX Driver in USA.
Our PC-FAX drivers do not suit the USA Telecommunication Regulations. Good Luck

Thank you very much the scanner is working good in normal mode also,
And about the fax I have check it and I found I have problem in phone line so they need to come and fix it next week.

So thank you a lot, and I hope so the fax software will work after they will fix the phone line, and if no I will talk to you again.

Bye and thank you.

---

### Post by linuxwizard on 2008-03-04
You're Welcome Glad to hear scanner is working and hopeful it is just the phone line for your fax. Good Luck

---

