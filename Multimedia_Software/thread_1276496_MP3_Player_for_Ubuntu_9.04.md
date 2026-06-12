---
title: "MP3 Player for Ubuntu 9.04"
date: 2009-09-27
forum: Multimedia Software
---

### Post by daithi81 on 2009-09-27
Hello, i recently migrated (again) to Ubuntu. I am trying to setup a media player to play my mp3's, which are situated on the Windows side of my HDD. I have tried using Amarok and JuK, but neither seem capable of doing this. Amarok won't add files to it's library, even when I bring the file over to the Ubuntu side, and JuK will add the file only when brought over, but won't play it. These are just run-of-the-mill MP3's, that have no problems on Windows apps.

Any ideas?

---

### Post by SuperSonic4 on 2009-09-27
I assume the drive with the music on is mounted?

You will also need the *ubuntu-restricted-extras* package

---

### Post by daithi81 on 2009-09-27
> **SuperSonic4 said:**
> I assume the drive with the music on is mounted?

You will also need the *ubuntu-restricted-extras* package

Yes, it is mounted on the desktop. I have installed the package you mentioned, but when I use:

Amarok>Settings>Configure Amarok>Collection and then select my music folder in Windows, nothing happens.

---

### Post by SuperSonic4 on 2009-09-27
I assume you've given it enough time to scan. It could be an issue with Phonon's backends though. Do any GTK apps or VLC play them?

---

### Post by daithi81 on 2009-09-27
> **SuperSonic4 said:**
> I assume you've given it enough time to scan. It could be an issue with Phonon's backends though. Do any GTK apps or VLC play them?

No, the scan doesn't happen in the first place.

I tried VLC with a file from Windows and it played perfectly. I try the same with Amarok and nothing.

---

### Post by mcduck on 2009-09-27
Ubuntu doesn't come with MP3 codec by default (beacause it's not free but instead restricted by patents).

Just install the appropriate codecs and pretty much every media player you can find will play your files.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I wouldn't recommend using the ubuntu-restricted-extras -package unless you really want Java and Adobe reader as well. Just follow the instructions for installing the codecs. Also if you simply try clicking on media files in Gnome, or Gnome's default media player, it should ask if you want to install the required codecs.

---

### Post by daithi81 on 2009-09-27
> **mcduck said:**
> Ubuntu doesn't come with MP3 codec by default (beacause it's not free but instead restricted by patents).

Just install the appropriate codecs and pretty much every media player you can find will play your files.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I wouldn't recommend using the ubuntu-restricted-extras -package unless you really want Java and Adobe reader as well. Just follow the instructions for installing the codecs. Also if you simply try clicking on media files in Gnome, or Gnome's default media player, it should ask if you want to install the required codecs.

I tried to install the codec when Rhythmbox prompted me to, but when it tried to do this it said the codec was not available. The link you provided says nothing about my version of Ubuntu, which instructions should I follow?

---

### Post by mcduck on 2009-09-27
> **daithi81 said:**
> I tried to install the codec when Rhythmbox prompted me to, but when it tried to do this it said the codec was not available. The link you provided says nothing about my version of Ubuntu, which instructions should I follow?

What version are you using, then?

---

### Post by daithi81 on 2009-09-27
> **mcduck said:**
> What version are you using, then?

As stated in ze title, 9.04 - The Jaunty Jackalope.

---

### Post by mcduck on 2009-09-27
> **daithi81 said:**
> As stated in ze title, 9.04 - The Jaunty Jackalope.

Then you should read the page I linked again. It definitely gives instructions for 9.04. :)

Anyway, what oyu really need to do, is just install a bunch of gstreamer codec packages. you can search for them in Synaptic Package Manager (System->Administration->Synaptic Package Manager") or in Applications->Add/remove. If you use the Add/remove -tool make sure you set it to show "All available applications", then just do a search for gstreamer.

If you still can't find them, or they don't install, go to System->Administration->Software sources, and make sure you have all repositories enabled on the Ubuntu Software-tab.

---

### Post by fela on 2009-09-27
In amarok you might have to go to the tools menu, then 'rescan collection' and/or 'update collection'. It should provide a progress bar at the bottom. Then all your music appears in the collection browser.

What about rhythmbox though?

---

### Post by SuperSonic4 on 2009-09-27
If you look in synaptic what comes up as installed when you search for "Phonon"

For me it is ```
kdemod-phonon-backend-gstreamer
phonon-backend-mplayer
phonon-backend-xine
phonon-vlc-svn 1013055-1

```

---

### Post by daithi81 on 2009-09-27
> **mcduck said:**
> Then you should read the page I linked again. It definitely gives instructions for 9.04. :)

Anyway, what oyu really need to do, is just install a bunch of gstreamer codec packages. you can search for them in Synaptic Package Manager (System->Administration->Synaptic Package Manager") or in Applications->Add/remove. If you use the Add/remove -tool make sure you set it to show "All available applications", then just do a search for gstreamer.

If you still can't find them, or they don't install, go to System->Administration->Software sources, and make sure you have all repositories enabled on the Ubuntu Software-tab.

Ok, I already installed the ubuntu-restricted-extras package and some of the gstreamers are already installed in the Synaptic Manager, but there are about 20 of them, some are not installed. In the add/remove section, all but the mpeg2 streamer is installed.

---

### Post by daithi81 on 2009-09-27
> **SuperSonic4 said:**
> If you look in synaptic what comes up as installed when you search for "Phonon"

For me it is ```
kdemod-phonon-backend-gstreamer
phonon-backend-mplayer
phonon-backend-xine
phonon-vlc-svn 1013055-1

```

For me:

```
Phonon
Phonon-backend-xine
libphonon4
```

---

### Post by daithi81 on 2009-09-27
Ok, got it working. I just copied your packages.

thanks everyone.

---

