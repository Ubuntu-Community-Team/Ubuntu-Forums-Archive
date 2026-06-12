---
title: "SVIDEO output goes black once mythbuntu loads"
date: 2008-02-10
forum: Mythbuntu
---

### Post by kmuldrew on 2008-02-10
When I switch from using a monitor to using the svideo output of an NVIDEA GeForce 2MX AGP card, everything goes well until Mythbuntu loads. As soon as the progress bar reaches the end, the screen goes black and stays black (on this tv an absent signal is blue, so there is a signal, just no mythtv frontend nor an ubuntu window). If I go back to a monitor and alter the appearance setup to use a different window size for TV and for the ubuntu window, then the svideo output will work. Once mythtv starts, then I can go back into the appearance setup and reset the window size to the default so that it fits on the screen. After this, everything works fine, but it means that a monitor must be used whenever the machine restarts. Any ideas as to why the card goes black?

Mythbuntu 7.10, Hauppage pvr-150, Nvidea Geforce 2MX.

---

### Post by Titus A Duxass on 2008-02-11
Try (when connected to the TV only) going into a virtual terminal with Ctrl+F1 (e.g.) and then running "sudo dpkg-reconfigure xserver-xorg).

When its finished restrat your orignal xserver by exiting the virtual terminal and going back with Ctrl+F7.

Sometimes a reboot after running the above command helps as well.

---

### Post by theacoustician on 2008-02-11
> **kmuldrew said:**
> When I switch from using a monitor to using the svideo output of an NVIDEA GeForce 2MX AGP card, everything goes well until Mythbuntu loads. As soon as the progress bar reaches the end, the screen goes black and stays black (on this tv an absent signal is blue, so there is a signal, just no mythtv frontend nor an ubuntu window). If I go back to a monitor and alter the appearance setup to use a different window size for TV and for the ubuntu window, then the svideo output will work. Once mythtv starts, then I can go back into the appearance setup and reset the window size to the default so that it fits on the screen. After this, everything works fine, but it means that a monitor must be used whenever the machine restarts. Any ideas as to why the card goes black?

Mythbuntu 7.10, Hauppage pvr-150, Nvidea Geforce 2MX.

It sounds like you're starting at too high a resolution.   Svideo is limited to NTSC resolution (640x480) and not every card will scale the output appropriately.  So you might have to set your start up resolution to 640x480 to get the results you're looking for.

---

### Post by kmuldrew on 2008-02-11
Titus, ctrl-F1 didn't get me off the black screen. I typed in the reconfigure command anyway but nothing happened.

Theacoustician, I think I tried that and it started up as a small window (which could be fixed by going back and adjusting the width and height to 0, 0 for the default). I may be misremembering though so I'll try it again right now.

Thanks for the suggestions,

---

### Post by kmuldrew on 2008-02-11
No joy; setting the GUI size to 640 x 480 brings up the black sreen. The only thing that seems to work is to set a different size for TV and the GUI while using a monitor and then go back and turn that option off once mythbuntu has started on the svideo output.

---

### Post by david.birch on 2008-02-11
Hi,
   not sure if this applies for ur card (i have 7300 GS), but i had to force detection in xorg.conf when using the nvidia binary driver, you can see some options here [http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/appendix-b.html)

I had extra options in my screen section of xorg.conf something like

        Option "ConnectedMonitor" "TV"
        Option "UseDisplayDevice" "TV"
        Option "UseEDID" "false"
        Option "ModeValidation" "NoEdidModes"

hope it helps

---

