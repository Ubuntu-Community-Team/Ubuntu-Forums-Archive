---
title: "can't install printer drive on mythbuntu??"
date: 2009-04-28
forum: Mythbuntu
---

### Post by Arminius on 2009-04-28
hey, my printer is a canon pixma ip4200.

I went to the website and downloaded the cnijfilter-common-2.60-3.i386.rpm

I followed some instructions to convert it to a .deb file.

but nope, didn't work, no printer is showing up.

so any advice?

---

### Post by klc5555 on 2009-04-28
> **Arminius said:**
> hey, my printer is a canon pixma ip4200.

I went to the website and downloaded the cnijfilter-common-2.60-3.i386.rpm

I followed some instructions to convert it to a .deb file.

but nope, didn't work, no printer is showing up.

so any advice?

There's a 3rd party driver already in DEB format dating back to the Edgy Eft days that may (or may not) work for you. Instructions and download from here: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Good luck.

---

### Post by Arminius on 2009-04-29
ok, I don't know why windows is so printer friendly and mythbuntu has to be so printer unfriendly, none of those instrcutions were newb friendly.

ok, I went to software sources and added "deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./"

is that right?

then I went to terminal and ran "# apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj"

and nothing happened? so where am I going wrong.

---

### Post by klc5555 on 2009-04-29
> **Arminius said:**
> ok, I don't know why windows is so printer friendly and mythbuntu has to be so printer unfriendly, none of those instrcutions were newb friendly.

ok, I went to software sources and added "deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./"

is that right?

then I went to terminal and ran "# apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj"

and nothing happened? so where am I going wrong.

This is not a printer I use --I just knew about the existence of a driver. You're right insofar as oddball inkjet printers are frequently a pain in the tookis to get running in Linux. And oddball lasers are no fun either.

But my initial guess is that after adding the source repository you didn't run  'sudo apt-get update'    (the '#' in the developer's version of the command implies that the apt-get commands should be run from a root prompt. Ubuntu prefers 'sudo' for this, and will then prompt you for the password.)

Likewise, when attempting to load the filter itself, the way you'd enter the command in Ubuntu is more likely something like:

sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj

Good luck!

---

### Post by Arminius on 2009-04-29
thanks for trying klc5555
but I entered "sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj" into terminal
it installed something big, but still no printer working, so I reboot, and still no printer working.

any other ideas?

---

### Post by klc5555 on 2009-04-30
> **Arminius said:**
> thanks for trying klc5555
but I entered "sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj" into terminal
it installed something big, but still no printer working, so I reboot, and still no printer working.

any other ideas?

Now, logically, I'd recommend from the desktop going back into the System menu (perhaps slightly differently labelled depending on your version and flavor of Ubuntu), then into Printing and try to the usual "add printer" process there. This is the Ubuntu gui for the Cupsys process the developer talks about, that other more techie distros would have you doing directly. To quote the developer:

"Cupsys will be automatically restarted and you can select printer in cupsys configuration ([http://127.0.0.1:631/](http://127.0.0.1:631/)). Vendor is Canon and Driver is, for example, "Canon PIXUS iP8600 ver.2.5".

"I received reports that these printers also worked with this driver.

    * Canon BJ S700 (with iP3100 driver)
    * Canon Pixma 3000 (with iP3100 driver)
    * Canon PIXMA MP750, MP780 (with iP4100 driver)"



If the driver fails to show up at all in the Printer configuration tool, or if you add the printer successfully but still can't get it to print ...well, the developer says the driver was designed for Debian and for Ubuntu 6.something. It could possibly no longer be compatible.

---

### Post by Arminius on 2009-04-30
there is no printing or anything print related in the system menu, or any menu.

---

### Post by klc5555 on 2009-04-30
> **Arminius said:**
> there is no printing or anything print related in the system menu, or any menu.

I suppose I should have asked this first: are you running Mythbuntu? Or Ubuntu with the Mythtv packages added? Since you were worrying about printing, which most people don't do from Mythbuntu proper, I assumed you were running Ubuntu + Mythtv.

If Mythbuntu proper, it has streamlined much of the strictly desktop PC stuff out, including most of the print sybsystem. You need to add the printing packages. The needed stuff is covered by the Ubuntu developer Superm1 in the thread "[SOLVED] Printing in Mythbuntu?" here: [http://74.125.47.132/search?q=cache:pC7ciTL24PgJ:ubuntuforums.org/showthread.php%3Ft%3D614138+%2Bmythbuntu+%2Bprinting&cd=1&hl=en&ct=clnk&gl=us](http://74.125.47.132/search?q=cache:pC7ciTL24PgJ:ubuntuforums.org/showthread.php%3Ft%3D614138+%2Bmythbuntu+%2Bprinting&cd=1&hl=en&ct=clnk&gl=us)

Add the packages Superm1 said in his post, and you should be ready to add your printer.

---

### Post by klc5555 on 2009-05-01
> **klc5555 said:**
> I suppose I should have asked this first: are you running Mythbuntu? Or Ubuntu with the Mythtv packages added? Since you were worrying about printing, which most people don't do from Mythbuntu proper, I assumed you were running Ubuntu + Mythtv.

If Mythbuntu proper, it has streamlined much of the strictly desktop PC stuff out, including most of the print sybsystem. You need to add the printing packages. The needed stuff is covered by the Ubuntu developer Superm1 in the thread "[SOLVED] Printing in Mythbuntu?" here: [http://74.125.47.132/search?q=cache:pC7ciTL24PgJ:ubuntuforums.org/showthread.php%3Ft%3D614138+%2Bmythbuntu+%2Bprinting&cd=1&hl=en&ct=clnk&gl=us](http://74.125.47.132/search?q=cache:pC7ciTL24PgJ:ubuntuforums.org/showthread.php%3Ft%3D614138+%2Bmythbuntu+%2Bprinting&cd=1&hl=en&ct=clnk&gl=us)



Sorry --the listserv software doesn't allow me to link to an old thread that way. But just do a search for  

[SOLVED] Printing in Mythbuntu?

and you'll find the thread and the post I'm talking about.

---

### Post by AlecJ on 2009-05-01
Would like to know how you got on with this.
And what you have found to print out?

---

