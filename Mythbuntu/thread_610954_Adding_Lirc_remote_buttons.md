---
title: "Adding Lirc remote buttons"
date: 2007-11-12
forum: Mythbuntu
---

### Post by ghuber on 2007-11-12
Ok,  I mapped some keys so that if I press F2 it jumps to the Videos section on MythTV.  Works great.

Lirc is working and I want to map some of the buttons on my remote to keys.  Such that the Videos remote button maps to F2 and brings up Videos screen in MythTV.  Simple enough.  So I check my lircd.conf and find this section:
> 
 name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
etc etc

I then run irw and see output like this:

> 00000000000001798 00 Videos Hauppauge_350

Looks good so I edit my /home/username/.lircrc file and add this to the end of it:


> begin
remote = Hauppauge_350
prog = mythtv
button = Videos
repeat = 0
config = F2
delay  = 0
end


begin
remote = Hauppauge_350
prog = mythtv
button = TV
repeat = 0
config = F4
delay  = 0
end

I reboot, the remote still works but the buttons don't do anything.  They still show up in irw but nothing happens.  

Am I forgetting something?

Thanks
Geoff

---

### Post by uopjohnson on 2007-11-12
Try editing ~/.mythtv/lircrc it controls buttons in myth.  The ~/.lircrc is probably a copy of that.

---

