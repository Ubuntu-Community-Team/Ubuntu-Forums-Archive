---
title: "Best way to convert LinDvd Rpm with Alien How?"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by cchester on 2008-04-02
Hey Guys,

I got a recent dvd edition of Linux Magazine that had Mandrivia Powerpack 2008 on it and it included LinDvd on it.

I want to covert the LinDvd rpm file to a deb file to install in Ubuntu 7.10.

What is the best way to do this with Alien so it will install correctly and work?

Thanks for any help.

---

### Post by xc3RnbFO8P on 2008-04-02
Copy the .rpm file to home folder
In Terminal:
> apt-get install alien
alien /home/your folder/lindvd.rpm
ls -l
dpkg -i /home/your folder/lindvd...all.deb


---

### Post by cchester on 2008-04-02
Thanks for the reply. I tried that and this is what I get.

"warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
Warning: Skipping conversion of scripts in package lindvd: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
warning: lindvd-1.2.6-8mdv2008.0.i586.rpm: Header V3 DSA signature: NOKEY, key ID 70771ff3
lindvd_1.2.6-9_i386.deb generated"

So any other ideas on how to convert this package? I get the following when I run lindvd after installing the package.

/usr/bin/lindvd: line 3: exec: soundwrapper: not found

Thanks for any more help.

---

### Post by xc3RnbFO8P on 2008-04-02
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=676197]("http://ubuntuforums.org/showthread.php?t=676197")

---

### Post by jimbob on 2008-04-02
I have a copy of the original lindvd_1.2.6-6_i386.deb that works fine for me on feisty, gutsy and hardy beta that I would be glad to upload somewhere for you if you are interested.  Then you wouldn't have to worry about converting.

---

### Post by cchester on 2008-04-02
> **jimbob said:**
> I have a copy of the original lindvd_1.2.6-6_i386.deb that works fine for me on feisty, gutsy and hardy beta that I would be glad to upload somewhere for you if you are interested.  Then you wouldn't have to worry about converting.

That would be great but I don't have anywhere you can upload it to. Can you do it through usenet?

Thanks again.

---

### Post by igknighted on 2008-04-06
Your original installation was fine.  All you need to do is open the file that failed (/usr/bin/lindvd) which is a script with 3 lines.  The third is the above mentioned 'exec soundwrapper /usr/share/lindvd/lindvd' line.  Delete the word "soundwrapper" and save the file (you need to have opened it with sudo).  Now try to run the program, it should load normally and work fine.

---

### Post by cchester on 2008-04-06
Thanks for the reply I will try that and let you know how it works out. If so is there a way to get the program not to do that after installing? A way to give it different commands when converting it with alien so that the script when it converts lindvd is suited for ubuntu.

---

