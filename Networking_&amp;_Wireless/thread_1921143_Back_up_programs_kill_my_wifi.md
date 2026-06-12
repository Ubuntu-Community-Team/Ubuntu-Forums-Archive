---
title: "Back up programs kill my wifi"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by sparhawkthesecond on 2012-02-06
I've been trying to back up my home folder to a wireless network drive (located on an Apple Airport Extreme), using either deja-dup or "Back in Time". In both cases, the backup seems to start fine, but after c. 30–60 minutes, my wifi dies. The wifi menu item says "Networking disabled", and clicking "Enable networking" doesn't do anything. If I do "sudo restart network-manager" it does restore the network, but there seem to be other issues in both cases, as I'll describe for each case below.

In the case of deja-dup, I mounted the drive "Wells" using
```
$ sudo mount -t cifs -o user=abc,password=xyz,dir_mode=0777,file_mode=0777 //192.168.1.2/Wells ~/mountpoints/Wells
```After restarting the crashed wifi, the backup appeared to remain stalled. I couldn't unmount the disk, as there was an "unkillable" duplicity process holding onto a file on it. The computer would not shutdown, so I had to cold power off. After restarting, I tried resuming the backup twice, with the same result.

I then tried "Back in Time", mounting the disk using
```
sudo mount -t cifs -o user=abc,password=xyz,rw,hard,nosetuids,noperm //192.168.1.2/Wells ~/mountpoints/Wells
```I can't exactly remember why I used these options instead, but backintime game me some error with the other options. I think it complained of being unable to store modification dates on the disk, or something similar. Anyway, with the new options, it started fine. This time, after restarting the dead network manager, the backup automatically resumed. After a while, it froze again. I restarted the computer, but now I could not mount any disk on the network. Terminal just moved the cursor to the next line, and froze. I restarted both the computer and the  Airport extreme router, then I could mount again.
I've just tried backing up again, and soon got the dead wifi. Again, restarting the manager resumed backup. Back in Time is still running, but even if it's completes fine this time, it's a bit irritating that backups are frequently aborted, especially as I intent to backup overnight. Would anyone have a solution?

Cheers.

---

### Post by sparhawkthesecond on 2012-02-10
To answer myself, the problem appears to be related to sleep settings. What alerted me was that I wouldd return to the computer, restart the network manager, then the computer would suspend immediately, although I'd just been pressing keys, etc. Previously, to prevent the computer from sleeping, I ran the following script (which is equivalent to using dconf).
```
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac false
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery false
```
Once I realised there was a problem, I tried setting sleep to "never" via the System Settings GUI, which also altered the settings below.
```
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 0
```Once I flipped both pairs of settings, all was good. A bit couterintuitive perhaps, but seems to work.
Now, if only "Back In Time" would complete a backup! It's been going for days, and appears to be very very slow!

---

