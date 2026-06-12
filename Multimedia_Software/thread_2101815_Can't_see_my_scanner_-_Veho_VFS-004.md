---
title: "Can't see my scanner - Veho VFS-004"
date: 2013-01-05
forum: Multimedia Software
---

### Post by vincewebb on 2013-01-05
I have a Veho VFS-004 slide and negative scanner connected to my computer which is running Ubuntu 12.04.  I have not used a slide scanner before but I expect to be able to use the "Simple Scan" application that I use for scanning paper documents.

Sadly the Veho scanner does not appear in list of source devices.


lsusb shows it as:
Bus 001 Device 009: ID 0ac8:c453 Z-Star Microelectronics Corp.

running: sane-find-scanner
finds my HP flatbed scanner but not this new scanner

This Veho scanner can be seen at:
[http://www.veho-uk.com/main/shop_detail.aspx?article=6](http://www.veho-uk.com/main/shop_detail.aspx?article=6)

Any ideas ?

---

### Post by xc3RnbFO8P on 2013-01-05
Check this:
[http://www.hamrick.com/]("http://www.hamrick.com/")

---

### Post by vincewebb on 2013-01-05
The link that Ringi suggests is to the company behind the proprietary VueScan scanner application. 

I'm not particularly keen on installing proprietary software but that is probably academic because Hamrick does not include Veho in the list of scanner manufacturers that VueScan supports.

---

### Post by xc3RnbFO8P on 2013-01-05
Maybe try this?:
[http://ubuntuforums.org/showpost.php?p=11123877&postcount=12]("http://ubuntuforums.org/showpost.php?p=11123877&postcount=12")
> I have found two ways to get it working.
Install cheese (either synaptic or from the command line with "sudo apt-get install cheese"
before starting cheese connect yur scanner to a USB port
start cheese and you should see a picture
the alternative is to install streamer (e.g. sudo apt-get install streamer)
once you have done that you can scan pictures from the command line with this command: streamer -f jpeg -o /path/to/image.jpeg

I get the best quality initial scan with cheese but you can always use GIMP to improve your images afterwards.

Who needs Windows with yet another being loaded all the time.

---

### Post by vincewebb on 2013-01-05
Well that sounds pretty mad, a webcam application ( Cheese ) to drive a scanner. Mad but it works and it's super quick.

I have no control over the resolution, all these old 35mm slides come out as 2592 x 1728 pixels, approx 550 to 850 KBytes. So that's not great but quick is good.

---

### Post by xc3RnbFO8P on 2013-01-06
What resolution option do you have in Cheese?

---

### Post by vincewebb on 2013-01-09
2592 x 1728

---

