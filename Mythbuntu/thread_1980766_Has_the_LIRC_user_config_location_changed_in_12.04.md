---
title: "Has the LIRC user config location changed in 12.04"
date: 2012-05-15
forum: Mythbuntu
---

### Post by pt123 on 2012-05-15
I was running LIRC on 10.10 using the Mythbuntu settings
in the ~/.lircrc file which includes files from ~/lirc folder. This was created by a package called mythbuntu-lirc-generator.
[http://manpages.ubuntu.com/manpages/hardy/man1/mythbuntu-lirc-generator.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/mythbuntu-lirc-generator.1.html)

I copied this set up for a regular ubuntu 10.10 machine and it worked fine. But after upgrading to 12.04 remote is not working with the applications. 
XMBC is working fine with the remote but it doesn't use the above config files setup to configure the LIRC. 

When I run irw it seems to be intepreting the keys fine.

When I tried to run Rhythmbox and use LIRC it kept reporting that it was unable to figure out the key pressed. I have a lirc config file for rhythmboxn in ~/.lircrc which worked fine with 10.10.

So I am guessing lirc is not using ~/.lircrc, is this correct, and if so what is the new location?

---

### Post by pt123 on 2012-05-15
The problem seems to have arisen after the button names for MCE remotes was changed in 11.10. 
[http://ubuntuforums.org/showpost.php?p=11382539&postcount=10](http://ubuntuforums.org/showpost.php?p=11382539&postcount=10)

---

