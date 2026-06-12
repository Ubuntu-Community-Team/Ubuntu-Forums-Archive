---
title: "Help with editing remote"
date: 2007-10-17
forum: Mythbuntu
---

### Post by kyfehr on 2007-10-17
I have been trying for three days to get my remote working correctly (MCE 1069, black, came with PVR 150 MCE Kit). 

The remote works, using the remote option mceusb2 and mceusb However, the key mapping is wonky. I did a search and found this website [http://www.hauppauge.co.uk/board/showthread.php?t=8048](http://www.hauppauge.co.uk/board/showthread.php?t=8048) that has info to change the remote and its buttons.

When I follow the directions I am stuck at how to copy the new files over the old lircd.conf and .lircrc or to change to these new files. I did do a sudo cp -f and get them to overwrite the old files, but when I reboot the remote does not work at all and I need to set it back to Windows MCE remote again.

I am really new to linux and am not that familiar with terminal - I just want to change the key mappings so that I can have the remote work correctly. For instance the channel up buttons right now skip forward and backward instead of change channel, and there is no key that changes between my two tuners.

Any help would be very helpful.

Oh... I am running the latest RC with updates. Everything else is working correctly to my knowledge.

Thank you in advance.

kyfehr

---

### Post by OffAxis on 2007-10-17
I believe there's an option on the mythbuntu desktop's drop-down menu to configure remotes. You can reset back to your original remote there.

---

### Post by superm1 on 2007-10-17
> **kyfehr said:**
> I have been trying for three days to get my remote working correctly (MCE 1069, black, came with PVR 150 MCE Kit). 

The remote works, using the remote option mceusb2 and mceusb However, the key mapping is wonky. I did a search and found this website [http://www.hauppauge.co.uk/board/showthread.php?t=8048](http://www.hauppauge.co.uk/board/showthread.php?t=8048) that has info to change the remote and its buttons.

When I follow the directions I am stuck at how to copy the new files over the old lircd.conf and .lircrc or to change to these new files. I did do a sudo cp -f and get them to overwrite the old files, but when I reboot the remote does not work at all and I need to set it back to Windows MCE remote again.

I am really new to linux and am not that familiar with terminal - I just want to change the key mappings so that I can have the remote work correctly. For instance the channel up buttons right now skip forward and backward instead of change channel, and there is no key that changes between my two tuners.

Any help would be very helpful.

Oh... I am running the latest RC with updates. Everything else is working correctly to my knowledge.

Thank you in advance.

kyfehr
When you copied the files over, make sure that they were copied to the right places.

The lircd.conf goes in /etc/lirc/lircd.conf

The lircrc goes in ~/.mythtv/lircrc

You have to restart lircd and then logout/in for the changes to take effect.

```
sudo /etc/init.d/lirc restart
```

Should you get things working with this other remote configuration, please file a bug in launchpad with a summary of your remote, what mappings don't work, and attach the functional files to the bug.
[https://bugs.launchpad.net/mythbuntu/+filebug](https://bugs.launchpad.net/mythbuntu/+filebug)

---

### Post by superm1 on 2007-10-17
Now mind you if all the buttons "work" but are just mapped funny, you can manually modify ~/.mythtv/lircrc

Each of the mapping is hand editable and should be pretty straightforward to follow.

---

### Post by kyfehr on 2007-10-17
Thanks for your help.. I missed the reset of the lirc.. that worked.. need to work on the mapping though, but it is better than it was

---

### Post by rusty0101 on 2007-10-18
Just as a followup recommendation, you may want to provide feedback regarding the button mapping to the appropriate group for your remote.

Also if you are having problems determining what button you want mapped to a feature, i.e. you know it's button x, but what is the label for button x that appears in .lircrc, you can use the irw command to get what lirc is reporting as the button pressed. It will almost always be the last column on the right. To use irw either switch to a console screen ([Ctrl]-[Alt]-[F1]) and log in, or open a terminal session at the desktop. Type irw then press enter. Now start pressing keys on the remote, moving it for gyroscopic controls, etc. You should see lines appear with information about what the remote is sending to the computer. That last element on the line is what you need to match up for in the .lircrc file.

The reason I note this is that some remotes list buttons differently than you might expect. The right arrow button to the right of the 'OK' button may be 'Chap+' rather than 'Right' for example. If you want it to be 'right' you will need to edit the appropriate button entry to reflect that.

-Rusty

---

### Post by apauna on 2007-10-18
Hello,

I have just finished the install of mythbuntu with a Hauppauge 350 card and wanted to map Back/Exit to Esc rather than 'D'. I have the grey remote Model # A415-HPG with the color buttons at the bottom. I did all the usual stuff

[LIST]
[*]placed the modified file in ~mythtv/.mythtv directory. Even chown to mythtv on the file
[*]restarted lirc and even restarted the PC.
[*]removed lircrc all-together and restarted lirc. This did cause myth to not respond to keys any longer, but when I put the modified file back myth still sees back/exit as 'D' and not Esc
[/LIST]

What am I doing wrong in the mapping file? :confused:

I have also attached my lircrc to this reply

Orig lircrc:
> 
begin
    remote = Hauppauge_350
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

Modified lircrc:
> # Escape/Exit/Back
begin
 remote = hauppauge_350
prog = mythtv
button = Back/Exit
config = Esc
end

---

### Post by superm1 on 2007-10-18
The ~mythtv user isn't used for anything but the backend in mythbuntu.

Put it in ~/.mythtv/lircrc

---

### Post by apauna on 2007-10-19
Thanks superm1 that helped! I forgot to mention I was doing this via ssh in putty on a windows pc. So to do the above I just went to a terminal on the mythbuntu and used the cmds from there. I was getting confused as to what user to use. That is why I used ~mythtv, but now I see that it works there as well. Again thanks for the help and quick response! :guitar:

---

