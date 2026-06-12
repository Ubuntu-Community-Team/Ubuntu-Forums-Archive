---
title: "Amarok: The process for the file protocol died unexpectedly"
date: 2010-06-26
forum: Multimedia Software
---

### Post by DThurman on 2010-06-26
[I don't know if this is the right solution, but apparently
 Amarok was unable to directly connect the sound device,
 that is, HDA Intel (ALC662 rev1 Analog) even though testing
 this directly worked within the 'Configure Phonon' menu,
 so I moved the Phonon Server & Jack Audio Connection Kit
 to the top of the device list, and it worked.
]

Amarok was running good after a fresh installation, but
after installing some programs, somehow I got a couple of
errors reported from Amarok.

1) When starting up Amarok, a popup message displayed:

   HDA Intel (ALC662 rev 1 Analog) failed, reverting to
   HDA Intel (ALC662 rev 1 Digital)

   I went into: Settings-> Configure Amarok->Playback->Configure Phonon
   and directly tested Analog and it works, and tested Digital and
   it does not work.

2) A pop up within the Amarok application says:
   "The process for the file protocol died unexpectedly"

I reinstalled:
   # apt-get --reinstall install \
         libxine1-ffmpeg \
         gstreamer0.10-plugins-ugly \
         ubuntu-restricted-extras
and this does not help...

What do I need to do to fix Amarok or Phonon?
[Never mind, it now works]

---

