---
title: "Problem Ubuntu 9.04 Firefox 3.0.8 and Youtube"
date: 2009-04-19
forum: Multimedia Software
---

### Post by mmicoe on 2009-04-19
Hello:
My computer 2 days ago:
Ubuntu 8.10 (Studio) Firefox 3.0.X and Youtube everything working perfectly.

Now: 
Ubuntu 9.04 Firefox 3.0.8 and I have a problem in youtube with the install_flash_player_10_linux.tar.gz --> **youtube works blows when window maximizes.**
I have tested with install_flash_player_9_linux.tar.gz but the mozilla firefox browser force quit and the browser disappears.

Any idea ow can I solve the problem ?

Thanks
Mauro:P

---

### Post by Bakon Jarser on 2009-04-19
I assume you are using an intel graphics card?

[https://bugs.launchpad.net/ubuntu/+bug/346289](https://bugs.launchpad.net/ubuntu/+bug/346289)

---

### Post by mmicoe on 2009-04-19
Hello:
Dell laptop Inspiron 9400:
VGA compatible controller: nVidia Corporation GeForce Go 7900 GS

Thanks
Mauro

---

### Post by Bakon Jarser on 2009-04-19
I'm going to guess that it is a conflict between video acceleration and compiz.  Try turning off desktop effects and see if that fixes it.  If it does and you don't care about desktop effects then that is your fix.  If you can't live without desktop effects you could try turning off video acceleration in flash (right click on a flash app and click properties).  Another option that might fix this is to upgrade to the 185.19 beta nvidia driver.  I've been using it for a couple of weeks with no issues.

---

### Post by mmicoe on 2009-04-19
I disabled desktop effects and has been fixed.
A very simple but effective solution.
It is strange that with Ubuntu 8.10 and compiz worked well with Ubuntu 9.04 and it is not.
I'm using Ubuntu for over 3 years and I'm very happy for this operating system.

Thank you very much Bakone Jars

---

### Post by hcuriel on 2009-04-27
Some guys already found the solution. Among them, in case you are reading this from a Linux x86 based putter: 
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/](http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/)
  
(For a 64b system, simply uninstall: **[COLOR=#17365d][FONT=&quot]sudo apt-get remove swfdec-mozilla[/FONT][/COLOR]**  
  And then reopen Firefox, let the system find and suggest to install the default player and voilá. It will work beautifully.)


*Taken from: [http://businerdss.blogspot.com](http://businerdss.blogspot.com)

---

### Post by Soundler on 2009-11-03
Yay, problem solved! Thanks. All I had to do is to unistall one plugin.

[]("http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/")

---

### Post by Soundler on 2009-11-03
> **hcuriel said:**
> Some guys already found the solution. Among them, in case you are reading this from a Linux x86 based putter: 
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/](http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/)
  
(For a 64b system, simply uninstall: **[COLOR=#17365d][FONT=&quot]sudo apt-get remove swfdec-mozilla[/FONT][/COLOR]**  
  And then reopen Firefox, let the system find and suggest to install the default player and voilá. It will work beautifully.)


*Taken from: [http://businerdss.blogspot.com](http://businerdss.blogspot.com)

Exactly ;) Found that myself and that worked. Thank all of you for the help! :popcorn:

---

