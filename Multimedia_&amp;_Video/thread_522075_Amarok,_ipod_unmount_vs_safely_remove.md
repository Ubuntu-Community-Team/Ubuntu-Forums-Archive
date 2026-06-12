---
title: "Amarok, ipod unmount vs safely remove"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by halfB on 2007-08-10
I use amarok in kubuntu for my ipod.  When the ipod is mounted automatically I get a "Safely Remove" option over the ipod icon.  When I connect the ipod within amarok I still get the "Safely Remove" option.  But when I click "unmount" from with in amarok the "safely remove" option disapears and I have to eject from within terminal.  Now if I don't  choose the "unmount" option within amarok but simply close amarok then the "safely remove" persists and works.  I would prefer to not have to close amarok to eject my ipod.  Any suggestions?  
I suspect it is a bug in amaroks unmout command.

---

### Post by halfB on 2007-08-10
Correction: the amarok does not have an Unmount option.  It is "disconnect."
HalfB

---

### Post by TryMe on 2007-09-01
you might try editing the  PostDisconnectCommand option for your ipod in the amarok config file 
/home/<user name>/.kde/share/config/amarokrc

something like this should work:
PostDisconnectCommand=echo "<your password>" | sudo -S eject -m %d

I have found the editing the option through the GUI does not work.

---

### Post by halfB on 2007-10-05
I found this works as it should in Gutsy.
Thanks
E HalfB

---

### Post by mkwerner on 2008-03-11
Sorry to drag up an old thread, but I just wanted to thank you both - I was having the same issue with amarok and a 1gb ipod shuffle.  Adding the command above to:

Settings->Configure Amarok->Media Devices->Settings->PostDisconnect Command box

fixed my issue and I'm golden with my ipod in Kubuntu now!

Cheers, and take care,
M.

---

### Post by NotoriousTF on 2008-03-23
I know this is an old thread but I'm having some problems with my iPod Shuffle. I entered the above command as mkwerner said worked for him but when I try disconnect from within Amarok, only my cd tray is ejected?!
Any ideas why?

---

### Post by bleaked on 2008-05-01
I just wanted to say that this fixed a rather frustrating issue with Hardy.  Thank you so much!

I feel I should also note that I was able to input this disconnect command from within Amarok and did not need to manually edit the config file.

.:bleaked

---

