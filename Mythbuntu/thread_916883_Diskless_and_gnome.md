---
title: "Diskless and gnome"
date: 2008-09-11
forum: Mythbuntu
---

### Post by RoyalPro on 2008-09-11
On my backend/frontend/diskless server I first I tried to install "Ubuntu" from the MCC.  It seemed to only install part of it.  I did it before with a previous install and was able to get gnome fully working and it installed all of the other things typical of Ubuntu.  I only have part of them installed that I can see in the standard Mythbuntu desktop and if I change the session to gnome in the login menu it just returns to the login menu.  If I try to install gnome with synaptic it tells me it needs gnome-desktop-environment. If I try to install gnome-deskop-enviroment it tells me it needs gnome-keyring-manager.  There is a gnome-keyring(installed) but no gnome-keyring-manager.

Not sure if this is related to it or not but my diskless clients can no longer load the login menu on a real computer.  It hangs with the cursor in the top left corner.  It works in a VM now but I was getting an error with the VM about it not being able to load X.  Didn't change anything in it to stop the error message it just started working again in the VM.

---

### Post by anonymousdog on 2008-09-11
So...um...what's the status of this? I'm having a hard time decoding your post :)

I can't tell if you're trying to get gnome/ubuntu desktop on the diskless clients or on the backend.  Which is working (if either)?

---

### Post by RoyalPro on 2008-09-11
On my backend/fronted/diskless server I can't get gnome to install. That is were I get the messages saying that it needs gnome-desktop-environment and that the environment needs the manager and there is no manager.  I first tried to get in installed with MCC using the "Ubuntu" check box, but it seemed to only do a partial install and a uninstall/reinstall didn't fix it.

The diskless was working but now it will only load the login menu and desktop on a VM and with a real comp it hangs with a cursor flashing in the top corner.

Could using the nvidia drivers cause a problem?  This all seemed to start after I started using them.
Sorry if my post is a bit rambling I just got home from a long night at work.

---

### Post by RoyalPro on 2008-09-11
Also can installing this using a SSH connection cause problems?  This is how I tried to do the installs.

---

### Post by anonymousdog on 2008-09-11
Not an X expert, but I could see where it might.  How are you running the MCC in an ssh session?  I could see where that might create all kinds of auto-config issues.

---

### Post by RoyalPro on 2008-09-11
ssh -CX mythm
the C is not needed
after login I just do a "sudo mythbuntu-control-centre"
I used to use XDMCP when I had normal Ubuntu installed on it.

---

### Post by laga on 2008-09-12
You can reset your diskless client by deleting directories in /var/cache/mythbuntu-diskless/overlay. However, you will lose all your settings.

---

### Post by RoyalPro on 2008-09-12
I changed the network interface on my mother board for the diskless client from the Yukon to the Nvidia and now it works.  Deleting the directories didn't help the Yukon to finish booting.

Still having problems getting gnome to install or the full "Ubuntu" to install from the MCC on the backend/fronted/diskless server.

---

### Post by RoyalPro on 2008-09-12
Well now after many attempts using MCC install and uninstall "Ubuntu Desktop" When at the login menu and I change the session to gnome it just logs me into the standard Mythbuntu Desktop instead of kicking me back to the login window.
In synaptic gnome/gnome-desktop-environment are not install.

---

