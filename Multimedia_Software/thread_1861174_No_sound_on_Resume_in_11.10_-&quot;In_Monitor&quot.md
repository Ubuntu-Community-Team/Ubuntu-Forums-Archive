---
title: "No sound on Resume in 11.10 -&quot;In Monitor&quot; Switches Off"
date: 2011-10-15
forum: Multimedia Software
---

### Post by enseyn on 2011-10-15
Okay. I have a Turtle Beach RIVIERA PCI Sound Card. After resuming from Suspend or Hibernate "S/PDIF In Monitor" is switched off. This causes the speakers on my computer desk to stop working, but the surround sound system for the TV does still work.

I also had this problem in 11.04, but it was easier to fix with gnome-alsa-mixer. Now I have to open up alsamixer in terminal to turn my speakers back on.

Any solution to this or work around would be much appreciated.

Also, I should say that in 11.04 the sound would be muted on resume as well.

---

### Post by enseyn on 2011-10-16
FIXED IT!!!
Okay, I used [This guide]("https://help.ubuntu.com/community/SoundTroubleshooting") and combined a couple parts to get it working. 

I used this part:
> Getting ALSA to work after suspend / hibernate

Some soundcards does not work after the computer has been suspended or hibernated. Files in /etc/pm/sleep.d/ are read when the system is entering or leaving suspend mode. Create a file telling the system to restart alsa when the computer is being brought up from suspended mode to make the audio work again.

The command /sbin/alsa force-reload will kill all running programs using the sound driver so the driver itself is able to be restarted.

sudo nano /etc/pm/sleep.d/50alsa

case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload
                ;;
        *) exit $NA
                ;;
esac

Make the newly created script to be executable with the following command:

sudo chmod +x /etc/pm/sleep.d/50alsa

At first it didnt work, but then I thought, Why am I not just reloading the settings with alsactl? So I changed /etc/pm/sleep.d/50alsa to this:

> case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsactl -F -f /var/lib/alsa/asound.state restore 
                ;;
        *) exit $NA
                ;;
esac

And Voilà! Working sound on resume.

---

