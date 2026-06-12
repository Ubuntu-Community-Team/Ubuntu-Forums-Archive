---
title: "Skype problems ( doesnt react )"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by lanchongzi on 2007-02-09
hi to all of you 

i just downloaded Skype in Xubuntu and installed it ( no problems here )
it even shows the icon in the Application/network menu
but when i click on it nothing happens - not even a message box

what do I do wrong?:confused:

---

### Post by scrooge_74 on 2007-02-09
try typing skype from a terminal window to see if there is any error message

---

### Post by lanchongzi on 2007-02-09
i tried that, but its the same - no reaction whatsoever

---

### Post by Cappy on 2007-02-09
Did you install it through automatix2? I've had problems using other methods before.

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt")

---

### Post by scrooge_74 on 2007-02-09
I stay away of automatix and such i have seen to may post of problems after using automatix.  I manage to install skype with no problem following the instructions in their website

---

### Post by lanchongzi on 2007-02-10
i did the same thing ( following their instructions ) and it worked, but just once!
the second time no reaction, and still no reaction.
does it have anything to do with other programms ( like SKIM that language program ) i have installed?

is there a way to check whats wrong?

---

### Post by ushaba on 2007-02-10
it may have to do with skim. i'm guessing you're using chinese from your name, but usually you get some informative error messages back from the terminal. search for a post on "scim, skype" and you should find previous posts about this. skim and scim have similar problems in their respective environments. another option is installing skype from the tar file on the skype site, which is more up to date than the one in the repositories, and may get around some of the problems people experience.

---

### Post by lanchongzi on 2007-02-10
iwill try that and will let you know how it went:) 

i have another question though.

I have Xubuntu installed, is there a way of changing it to Ubuntu?


if so i would appreciate the help


yhanks in advance

---

### Post by scrooge_74 on 2007-02-10
> **lanchongzi said:**
> iwill try that and will let you know how it went:) 

i have another question though.

I have Xubuntu installed, is there a way of changing it to Ubuntu?


if so i would appreciate the help


yhanks in advance

I  think you can do sudo apt-get install ubuntu-desktop and should do the trick

I installed Xubuntu just for kicks and since I use Skype try installing using the repository, gave me a weird message of another instance working (but that happen to me in the past), reboot and is working ok 

hope this helps

---

### Post by lanchongzi on 2007-02-10
just out of curiosity.
in Xubuntu do I have to type "sudo...."
or "gksudo....."  ?

---

### Post by lanchongzi on 2007-02-10
and YES there is a problem with scim and Skype
wouldnt you know   :)

"Ok, found the solution, sorry.
Just start skype from the command line as follows:

Code:

XMODIFIERS=@im=none QT_IM_MODULE=xim skype

What i just did is to enter this line in a shellscript.

Btw, this won't allow skype to use scim input method, it will just start skype in xim method. If you try to switch to scim, skype will just crash. This is a skype issue, and since it's not free software we'll have to wait for their developers to decide to fix it, if they ever do.
"


as posted by ]Nbx*cmD[

---

