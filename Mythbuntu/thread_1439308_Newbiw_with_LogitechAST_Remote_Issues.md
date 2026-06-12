---
title: "Newbiw with Logitech/AST Remote Issues"
date: 2010-03-26
forum: Mythbuntu
---

### Post by BobbyDing on 2010-03-26
Hi Folks,
Quick background.....I'm a complete newb to Myth and Linux. I know only a few basic Linux commands, but I'm working on it!!! Please bear with me. I just installed Mythbuntu on a Compac PC from the Live CD (latest version as of a week ago.... 9.10 I think). All the basics are working so far, except I cannot get my Logitech/AST remote to function (on serial comm 1). I set it up for that remote during the setup, and checked MCC after the install completed. It was selected there. According to the manual on page 112, there are some things that need to be done before Myth can use the serial ports for receiving from an IR device. Per page 112 section 12.2.1, from the terminal I did [COLOR=blue]'sudo apt-get install setserial'[/COLOR], which came back saying [COLOR=red]'setserial is already the newest version 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded'[/COLOR]. Then I did "[COLOR=blue]sudo dpkg-reconfigure setserial[/COLOR]' and selected [COLOR=blue]MANUAL[/COLOR]. The terminal came back saying [COLOR=red]'dpkg: warning: obsolete option '--print-installation-architecture", please use '--print-installation-architecture"[/COLOR]. After which /var/lib/setserial/autoserial.conf still says ###AUTOSAVE-ONCE at the top (was that file supposed to be updated to say MANUAL after that last command?). 
 
I've done some googling for this and cannot find out what the test in red above means. Do I need to install or reconfigure lirc first? Can anybody point me in the rite direction?
 
Thanks!!!

---

