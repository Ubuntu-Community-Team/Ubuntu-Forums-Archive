---
title: "Solution for using scanners under Natty"
date: 2011-10-04
forum: Multimedia Software
---

### Post by slumbergod on 2011-10-04
This guide is to help anyone who has found that their scanner won't work under Natty (11.04) OR Oneiric (11.10) - yes, that's right, after a clean install it is *still* broken. 

You might have installed sane and had it detected using "sudo sane-find-scanner" only to then be told no device was detected using "scanimage -L".

After seemingly endless searching and multiple attempts to get it working I finally found a solution. This is not my mine but it worked for my Artec eplus 48u USB scanner. The link to the original solution is here:
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475)
(huge thanks to Ashley Hooper!!!)

It turns out the solution is to replace two libsane packages with alternatives from debian repositories and to lock them so they don't get replaced. It has nothing to do with permissions.

Download the following: 

[http://ftp.us.debian.org/debian/pool/main/s/sane-backends/libsane_1.0.21-9_i386.deb](http://ftp.us.debian.org/debian/pool/main/s/sane-backends/libsane_1.0.21-9_i386.deb)
[http://ftp.us.debian.org/debian/pool/main/s/sane-backends-extras/libsane-extras_1.0.21.2_i386.deb](http://ftp.us.debian.org/debian/pool/main/s/sane-backends-extras/libsane-extras_1.0.21.2_i386.deb)

I'd suggest removing everything associated with scanning first:
sudo apt-get purge sane sane-utils xsane xsane-common

Then install the two packages you downloaded (assuming they are in a directory with no other deb packages you can use this command:)
sudo dpkg -i *.deb

Then as Ashely suggests, lock them so they are not upgraded to the newer (broken) Natty versions:

gksudo gedit /etc/apt/preferences.d/libsane

Paste these lines, then save and exit:

Package: libsane 
Pin: version 1.0.21-9
Pin-Priority: 900

Repeat the process for libsane-extras, making sure to change the name libsane for libsane-extras.

Confirm it works for both:

sudo apt-cache policy libsane

You'll get something like this:

libsane:
  Installed: 1.0.21-9
  Candidate: 1.0.21-9
  Package pin: 1.0.21-9
  Version table:
     1.0.22-2ubuntu1 900
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) natty/main i386 Packages
 *** 1.0.21-9 900
        100 /var/lib/dpkg/status

Then install the software purged above:
sudo apt-get install sane sane-utils xsane xsane-common

After this, plug in your USB scanner and test the commands from the top:
sudo sane-find-scanner
scanimage -L

If they work then fire up Xsane and select the scanner (in the list it presented me, both the scanner and my webcam were identified).

In 11.10, I had to do a couple more steps.
I copied the file Artec.usb to a new folder:
sudo cp /path-to-file/Artec.usb /usr/share/sane/

Then I needed to make sure it was readable by everyone:
sudo chmod o+r /usr/share/sane/Artec.usb

ls -l on /usr/share/sane/ should give something like
-rw-r--r-- 1 root root 8192 2011-11-11 13:31 Artec48.usb

Then finally it was working for me in both simple-scan and xsane.

Please, if you have any useful hints or suggestions add them here.

---

