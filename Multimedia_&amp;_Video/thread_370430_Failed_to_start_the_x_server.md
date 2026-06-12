---
title: "Failed to start the x server"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by stevenjo57 on 2007-02-25
Just when I thought I could use ubuntu as a replacement for XP. Even had Beryl working and was very impressed.

Installed Wine. Killed my video. Getting the message "Failed to start the x-server".

Reconfigured using the dpkg reconfigure xserver xorg thingy but had to use VESA server and all defaults.

Once I got VESA working, follwed the procedure here, [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

to reinstall the nvidia driver. Killed it dead again - same message. Suppose I could loop forever.

Any help appreciated.  Thanks.

---

### Post by moonshieldman on 2007-02-25
G'day stevenjo57,

I've had a problem where the permissions for /etc/profile are changed to non-executable which seems to stop X from loading.

If you're having the same problem, you'll be able to see the Ubuntu login screen, enter your username and password, and then it'll fail. Displayed will be a button that you can press to see the error messages.

To fix:
- Goto a console by pressing Ctrl + Alt + F1
- Login
- Then run:
```

sudo chmod 755 /etc/profile

```

But that's assuming you're having the same problems that i've had.

Good luck.

---

### Post by stevenjo57 on 2007-02-25
Thanks for your help.

Did not work.  I chmodded as you suggested.  I don't think it's the same problem. I never get to the login screen.

I neglected to mention that I'm using a GeForce 7300 GS.

I thought I'd try using the python script Envy.  So i reconfigured to VESA. INstalled Envy. The script runs.  I chose option 1 to install nvidia driver. Screen goes blank immediately and presented with a blinking cursor on a black screen. Won't accept commands. Let it sit for 30 minutes. Rebooted. Nothing changed.

More disappointment. Still stuck. Having to post this from a Windows machine.

---

### Post by stevenjo57 on 2007-02-25
More information. Probably futile.

I reconfigured to VESA.  Next I changed one thing in the xorg.conf.  I changed the "VESA" to "nvidia" and it breaks again.

Are my drivers corrpupt?

The highest resolution I have listed is 1024x768.

---

### Post by stevenjo57 on 2007-02-27
Decided to run "Envy" from the command line.  Seemed to run OK.

After reboot, the start x server seems to be OK.  Incorrect resolution, but I think I know how to fix it.

However, lots of other unusual things going on.  Can't administer because when I start a terminal window, it's just blank.  Just sits there.

Also, windows don't have close, minimize or maximize buttons.  Go figure. Have to close them using the File menu or double-click the window in the task bar to minimize it, then right-click to close.

Go figure.

---

