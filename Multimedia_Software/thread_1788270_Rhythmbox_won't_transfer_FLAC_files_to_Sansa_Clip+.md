---
title: "Rhythmbox won't transfer FLAC files to Sansa Clip+ : &quot;...strange filetype...&quot;"
date: 2011-06-22
forum: Multimedia Software
---

### Post by intheflesh on 2011-06-22
I have some problems when transferring files to my SansaClip+ 4GB. I'm using Rhythmbox on Ubuntu 10.10. Basically, the only way I'm able to get my player being recognized at any level is to select MTP mode (Auto doesn't work - lists Unknown device in Rhythmbox and the player just briefly displays Writing and then just stays there in silence with Connected being written on it's display). Also, I have to start Rhythmbox **first**, and then connect the player to a USB port (sometimes this too just doesn't work, so I switch ports - I guess it doesn't like having other devices attached to the same controller, but I might be wrong here). 

Anyway, the major problem is that **I'm unable to send .*flac* tracks to the device.** When I try to, I get the following message:

**Error transferring track**
Unable to send file to MTP device: LIBMTP_Send_Track_From_File_Descriptor(): I don't think this is actually a track, strange filetype...

The flac's have a .flac extension (*05 - Another Brick In The Wall [Part 2].flac* for example). The strangest thing is, **I can send mp3's** (haven't tried other supported formats because I don't have anything encoded in them) and I know the player supports FLAC (I had even used Rhythmbox on 10.04 to send FLACs without any problems!)

The other, a little less annoying problem is that **I can't see my µSD card in Rhythmbox. **Files stored on it are displayed on the list under Sansa Clip+ 4GB, but I can't control where I want to put new files (they get stored in Internal memory). When I right click on the device and select Properties, it displays the memory osed by 'songs' (that's Internal memory), then some 950MB marked as 'other' (that's my µSD card) and the free space appears to be combined free space Internal+External).

So, why don't I **just use MSC?** I can't. When I select MSC mode, I don't se any files on the Internal memory, neither on µSD card. The same is in Windows, so MSC mode is rather useless in my case.

I have the latest firmware (V01.02.15A), my system is up to date and last time I checked, everything worked fine on Windows XP (except for aforementioned non-working MSC mode).

So, how do I make Rhythmbox work with Sansa Clip+?

---

