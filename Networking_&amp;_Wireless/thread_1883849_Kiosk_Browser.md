---
title: "Kiosk Browser"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by createdcreature on 2011-11-20
For a Linux Kiosk, do you have any ideas of a suitable browser for my purpose explained in my '[Linux Kiosk]("http://ubuntuforums.org/showthread.php?t=1772311")' thread. I am currently using Firefox 4.0, and it is an absolute nightmare.

---

### Post by SteveDee on 2011-11-20
> **Robert Moyse said:**
> ...  I am currently using Firefox 4.0, and it is an absolute nightmare....

You don't say what your problems are with FF, so it make it rather difficult to advise.

Using Ubuntu as a basis for a Kiosk seems like "a sledge hammer to crack a nut".

I recently rolled out 50 thin clients using ThinStation software. Although you don't want a thin client, this software supports a web browser direct from the simple desktop. So in your case you could probably edit the conf files to remove all thin client options and just have it as web browser. The file size/image will be a small fraction of what you are using now.

If you are looking for a light-weight browser try Midori.

---

### Post by createdcreature on 2011-11-20
Well, I need the most basic browser possible that supports HTML5, CSS3, and JS. The problems with FF is that it has *way* too many features like add ons, and it is a HUGE target for fiddlers.

---

### Post by SteveDee on 2011-11-20
> **Robert Moyse said:**
> Well, I need the most basic browser possible that supports HTML5, CSS3, and JS...

OK so Midori is one option. You could try changing the permissions on /home/{user}/.conf to "read only". That may stop any changes sticking (i.e. once you re-boot the system is back to normal).

---

### Post by WasMeHere on 2011-11-20
Hi Robert,

You can also have a look at Webconverger
[[COLOR="RoyalBlue"]_http://webconverger.com/_[/COLOR]]("http://webconverger.com/")

Have fun finding out :-)
Olle

---

### Post by grg3 on 2011-11-20
If I understand you correctly, you are looking for a way to have the computer boot, open the browser full screen, and go to predetermined page. The easiest way to do this is to use Chrome or Chromium as your browser and take advantage of the [CODE]--kiosk[/CODE switch that is available when starting the browser. There is already a howto out there for Ubuntu [http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/")

I have even setup a chromium kiosk using Tiny Core Linux. Talk about small and light!:)

---

