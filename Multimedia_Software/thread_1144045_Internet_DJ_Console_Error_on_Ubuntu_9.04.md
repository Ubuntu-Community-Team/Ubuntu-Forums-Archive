---
title: "Internet DJ Console Error on Ubuntu 9.04"
date: 2009-04-30
forum: Multimedia Software
---

### Post by mckinlee14 on 2009-04-30
I use to DJ on windows with SAM Broadcast, so I came to Ubuntu and tried a program recommended to me by the forums, but It will not run. I get this box that comes up when I double click on the IDJC icon. It says:

The following programs were found to be missing...

metaflac from the flac package needed to play flac files
oggenc needed for the encoding of ogg/vorbis
ogginfo needed for ogg track length and tags
vorbiscomment from the vorbistools package

        Do you want to continue? 
                                
                  Yes       No

I selected yes and still nothing happens, can anyone help me?

---

### Post by markbuntu on 2009-04-30
You are missing some codecs. Open the Synaptic package manager and get

ubuntu-restricted-extras

And then follow this guide

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

IDJC should work after that.

---

### Post by bobince on 2009-04-30
What kind of server are you trying to stream to?

The version of idjc supplied with Ubuntu (intrepid or jaunty) is compiled without MP3 support (making streaming to a normal SHOUTcast MP3 server effectively impossible) and is pretty old; it has some fairly significant bugs especially (again) to do with SHOUTcast.

I'd recommend compiling a more up-to-date idjc from source if you want to use it for anything serious. This will involve installing a bunch of -dev packages if you haven't already. 1.0.13 is the best version at the time of writing; the new 1.0.14 includes a listener-number monitoring feature that annoyingly blocks the UI.

---

