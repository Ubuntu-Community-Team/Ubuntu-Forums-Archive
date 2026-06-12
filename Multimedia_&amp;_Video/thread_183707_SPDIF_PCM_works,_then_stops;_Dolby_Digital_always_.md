---
title: "S/PDIF PCM works, then stops; Dolby Digital always works"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by IRJustman on 2006-05-28
Hi, forumfolk!

I have a small-form-factor desktop I use as a set-top machine to play various media files.  When my new roomie brought her home theatre amp in, I hooked it up via S/PDIF, and everything worked, both uncompressed (stereo PCM) and compressed (Dolby Digital).  Now, for whatever reason, PCM does not work at all, while Dolby Digital still works fine.  I haven't tested dts as I have no dts content to test with.

I'm using a Sound Blaster Audigy (the original) which I've even changed it out with my Windows machine's card--which I know works via S/PDIF--to no effect.  It's the exact same card.  I used Alsamixer to switch whether I'm sending out via analog outputs or the digital jack which is copper coaxial, a method which has worked before.

I'm using Dapper with the absolute most recent versions of the kernel and Alsamixer.

Anyone have any ideas or suggestions?

Thanks!

--Ian.

---

### Post by IRJustman on 2006-09-25
I have no idea WHY it took me this long to figure it out, but here goes:

To do some additional troubleshooting, I took my Audigy and installed it in another Ubuntu box I have, my normal desktop Linux machine.  Digital out is fully functional.  I have some SBLives that I test in my set-top with.  Same story, everything works like it should.

I then did some noodling around to see where ALSA gets information about where to get information about the sound system's state when the system goes down.  I notice something when I stringsed the appropriate file that /etc/init.d/alsa-base runs:  /var/lib/alsa/asound.state.  I figure, let's wipe the file and start anew.  No go.

Finally, I got the thought, "Let's try a fresh install," only I used a different hard drive.  It fully works.  What I then did was to copy the /var/lib/alsa/asound.state file from the working setup and slip it into the non-working one.  Then everything woke right up; PCM and Dolby both work (still don't have any dts material to test with, though I now have my own home theatre amp and it, too, can decode dts).

Though now I'm using Edgy (I thought an upgrade would work; didn't); this likely would have worked in my former Breezy, then Dapper, setups as well; in fact, I translpanted my asound.state file from a Dapper setup into Edgy.

Hope this helps some poor soul who's going through the craziness I've been going through for the past few months!

--Ian.

---

### Post by PhatBoy on 2007-12-02
Thanks Ian, that saved me some time.

I have had the same problem with an Audigy 2 ZS under Gutsy.

It seems to me that ALSA writes to that file when you shut down which is why just deleting it and then rebooting doesn't work. Rather than get the file from a reinstall I booted from the Live CD and deleted the file on the hdd from there. Rebooting from the hdd and it worked (with all volumes also set to their kinda quiet default level).

:)

---

