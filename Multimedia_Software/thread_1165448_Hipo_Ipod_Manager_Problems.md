---
title: "Hipo Ipod Manager Problems"
date: 2009-05-20
forum: Multimedia Software
---

### Post by Azazel6662009 on 2009-05-20
hi all!  I'm somewhat new to the forum, so, if i overlooked this topic then, my mistake. 
I'm running Ubuntu 9.04 and was using gtkpod, but, switched over to Hipo because it was more comfortable for me to use. Everything WAS going well until today. While trying to apply the album art, as Hipo is saving, the program crashes with this message :

Failed to save database : Failed to save database : Argument is out of range.
Parameter name: value is less than 0

(details shows)
  at System.IO.FileStream.SetLength (Int64 value) [0x00000] 
  at IPod.PhotoDatabase.SaveThumbnails (System.Collections.Generic.List`1 existingNames, System.Collections.Generic.List`1 newNames, System.Collections.Generic.List`1 removedNames, IPod.ArtworkFormat format) [0x00000] 
  at IPod.PhotoDatabase.SaveThumbnails () [0x00000] 
  at IPod.PhotoDatabase.Save () [0x00000] 
::End of inner stack trace::
  at IPod.PhotoDatabase.Save () [0x00000] 
  at IPod.TrackDatabase.Save () [0x00000] 
::End of inner stack trace::
  at IPod.TrackDatabase.Save () [0x00000] 
  at Hipo.HipoMainWindow.SaveDB () [0x00000] 

now i'm not exactly a beginner with linux, i've dual-booted between Windows and red hat/mandrake/fedora (not all at once...lol) but i'm not an expert... VERY far from that obviously! 
But i am new to ubuntu (have been running it, alone...formatted the win partition!) for about 3 months now.
I've tried removing Hipo and reinstalling from within the terminal instead of synaptic. I've been told that with some programs, that can sometimes make a difference?
So has anyone else encountered this same error? and maybe found a fix?
Thanks for any help!

---

