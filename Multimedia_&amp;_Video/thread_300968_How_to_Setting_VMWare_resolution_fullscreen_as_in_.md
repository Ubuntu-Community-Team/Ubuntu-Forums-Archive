---
title: "How to: Setting VMWare resolution fullscreen as in Ubuntu!"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by MTZeon on 2006-11-16
I managed to have VMWare working with the same resolution that Ubuntu uses :) This works with every resolution set on Ubuntu, if it works on Ubuntu, it will work on VMWare Windows :)

- Open up VMWare, don't boot up Windows yet.
- Go to "View" and select "Autofit window" and "Autofit Guest".
- Close VMWare.
- Go to the terminal and do:
sudo gedit ~/vmware/preferences
- Now where it says:
pref.autoFitFullScreen = "fitHostToGuest"
change it to:
pref.autoFitFullScreen = "fitGuestToHost"

And thats it. Open VMWare, start your virtual machine, put it full screen. When you get to Windows, it will probably say that it can't set the resolution. On Windows, go to the monitor properties and you should be able to set the desired resolution :)

Enjoy!

---

### Post by Inferno. on 2007-01-11
I love you, it worked :mrgreen:

---

### Post by valermos on 2007-02-02
Thanks for the tip... it works great!

The only difference for me was my preferences file was not at ~/vmware/preferences   it was at ~/.vmware/preferences

Hope that helps anybody else.

---

### Post by era86 on 2007-09-04
Wow.. This really helped me out.  Thank you so much!

---

### Post by noworry on 2007-09-11
You are really great, it works superbly for me.

---

### Post by Krusader3z on 2007-09-25
Okay, this worked for the most part however, I was only able to go "Full Screen" at resolution 1024x768

Anything over that it it wouldn't go full screen.

I think I see what the problem is. My resolution in Feisty is 1440x900 and I do not see that resolution when I adjust the resolution on my virtual machine(Vista)

Anyone have any suggestions? Also, How do I get those borders i've heard about so I can spin my beryl cube?

Much thanks, 
Mike

---

### Post by NoVista on 2007-09-25
This worked great.
Started up the virtual machine and presto !

---

### Post by Mariano Oliveto on 2007-11-15
Krusader3z: I answered you in your post [http://ubuntuforums.org/showthread.php?t=559911&highlight=VMWare+resolution](http://ubuntuforums.org/showthread.php?t=559911&highlight=VMWare+resolution)

---

### Post by fenixphire07 on 2007-11-27
Hey thanks to valermos..i got freaked out when my sudo gedit ~/vmware/preferences came up wit a blank page...

Totally worked for me

---

### Post by fenixphire07 on 2007-11-27
Hi, I seem to having some trouble still. If anyone can help would much appreciate it. I changed the preferences accordingly but when i tried to switch to full screen an error occurs. I cant find the file indicated in the msg either.

Anyone who can help pls do. I have attached the msg shown as well.

btw, i'm running Ubuntu as host and Windows XP as client on my laptop computer. 128 Graphics Card Compaq Presario C300 Widescreen. 

Thanks.

Edit: I tried changing my xorg.conf file and with the word guest in the said sub section and oops GUI dnt load...lucky i made a back up of the file. Worked out that glich via CLI and so still locking for help.

---

### Post by fenixphire07 on 2007-11-27
Hi guys, firstly i'm not trying to spam this how-to forum. I think too much of the Ubuntu Forums and the help they provide to do so..

Anyway, if anyone has been having the trouble i mentioned in my earlier post, well if you do what has been specified in this how to , then your good to go. Dnt change the xorg.conf file or anything jus change the preferences and when u load your vmserver it will be in the correct resolution: rather it will be in the resolution of your host. 

Thanks to all.

---

### Post by dewycrim on 2008-03-10
It worked great after I realized that you meant to de-select Autofit Window and Autofit Guest. Just a minor detail, but it did trip me up for a while.:)

Another thing I noted was VMware seems to keep changing preferences file back. I couldn't think how to keep that from happening other than to change its permissions to "read only". - Any ideas?

---

