---
title: "Some DVD's wont play"
date: 2009-02-13
forum: Mythbuntu
---

### Post by lledurt on 2009-02-13
I have been working with mythbuntu 8.10 for a few months now and I thought that a few of my dvd's would never play (after being ripped or from the dvd) until I was using a remote front-end on ubuntu 8.04 they they worked great(ripped).

   I have installed the libdvdcss with medibuntu along with the others using the following link. ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)).  Great link by the way

This actually worked through a ssh tunnel, but wouldnt work on the native mythbuntu machine.  Because of that I am guessing it has something to do with the XFCE4 desktop.  Attached are my package lists if they help finding that missing lib.
Thanks
P.J.
[ATTACH]103222[/ATTACH]

[ATTACH]103224[/ATTACH]

---

### Post by lledurt on 2009-02-18
Bump,
And I have some more info.  Attached are the logs/terminal outputs when playing the file INC0NNF1.iso (a ripped version of The Incredibles)  The directory is shared to the other computers via NFS.  The file plays on the remote front end (ubuntu 8.04) (output working.txt) but will not play on the host (mythbuntu 8.10) (output notworking.txt)  The only difference I can tell between the 2 machines is the version of libdvdcss.  The newer one is the one not working.  Any thoughts  It looks like there are a few people out there having trouble playing newer DVD's  I am guessing it is related.

[http://ubuntuforums.org/showthread.php?t=896714&highlight=mythdvd+dvd](http://ubuntuforums.org/showthread.php?t=896714&highlight=mythdvd+dvd)

   I can actually play the DVD's and ISO using VLC so I know the codecs are there.  Andy thought?

---

