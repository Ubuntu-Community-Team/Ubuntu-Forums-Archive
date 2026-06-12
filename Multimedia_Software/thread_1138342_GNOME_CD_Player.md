---
title: "GNOME CD Player"
date: 2009-04-26
forum: Multimedia Software
---

### Post by graabein on 2009-04-26
I miss the CD Player that used to be installed as default. Anyone remember what it was called? GNOME something something? Can someone direct me to the package?

:confused:

Putting too many uses into a single bloated app sometimes works against its use. Starting **Banshee** or **Quod Libet** takes forever with huge collections or a slow computer. If I just wanna play an audio CD I'd rater open a specific app for that purpose.

Update: I'm using **Sound Juicer** for now.

---

### Post by logos34 on 2009-04-26
What the heck?  Gnome-cd used to be included in **gnome-media** pkg.  It's not there anymore.  Hmm...

> 
gnome-cd
gnome-sound-recorder
gnome-volume-control
gstreamer-properties
vumeter


Now (Hardy and after):

> This package contains a few media utilities for the GNOME desktop:

 * the GNOME GStreamer-based audio mixer;
 * a volume level meter for ESD;
 * the GNOME Sound Recorder;
 * the GStreamer properties capplet.


I use dcd (Dave's CD) from the CLI.  Ultralight, shows track ad album/cddb info...

> $ dcd -v
dcd 0.99.1 ("thinner") (C) 1998-2003 [email]dave@technopagan.org[/email] (GNU GPL)
Compiled on Jul  6 2006 with default drive /dev/cdrom
Includes MiniLZO 1.07 by Markus F.X.J. Oberhumer

$ dcd d
Track  Time  (24 tracks / 77:48) No Thanks! The 70s Punk Rebellion (disc 4)
   1   2:56  Hong Kong Garden                             
   2   2:22  Hanging on the Telephone                     
   3   3:22  Top of the Pops                              
   4   3:16  Adult Books                                  
   5   3:55  The Sound of the Suburbs                     
   6   3:28  California &#65533;ber alles                        
   7   3:03  Another Girl, Another Planet                 
   8   3:00  (I Want to Be an) Anglepoise Lamp            
   9   3:07  Radio Radio                                  
  10   3:56  Typical Girls                                
  11   2:15  Human Fly                                    
  12   4:21  Psycho Killer                                
  13   2:32  Babylon's Burning                            
  14   3:48  If the Kids Are United                       
  15   2:45  Alternative Ulster                           
  16   2:42  Boys Don't Cry                               
  17   3:24  She Is Beyond Good and Evil                  
  18   3:37  Is She Really Going Out With Him             
  19   2:44  Get Over You                                 
  20   3:19  Love Like Anthrax                            
  21   4:07  Peaches                                      
  22   3:17  Into the Valley                              
  23   3:04  You Can't Put Your Arms Around a Memory      
  24   3:25  Love Will Tear Us Apart


good luck

---

### Post by graabein on 2009-04-27
Thanks! That looks interesting. I'll give it a try. 

And that's an awesome collection of tracks you've got there! :)

---

### Post by Edectu on 2011-02-22
> **logos34 said:**
> What the heck?  Gnome-cd used to be included in **gnome-media** pkg.  It's not there anymore.  Hmm...


I use dcd (Dave's CD) from the CLI.  Ultralight, shows track ad album/cddb info...



 I used to use **dcd** every day, but it has also been removed and it's the only reason why I keep an older Ubuntu install alive. 
It's very useful in conjunction with [www.papercdcase.com]("http://www.papercdcase.com") for making uniformly readable CD track listings, complete with accurate track running times. 

 Why don't I use **cdcd** instead? 
I'll tell you exactly why! 

Compare the tracklisting above with the one linked here: 
[http://www.discogs.com/release/384475](http://www.discogs.com/release/384475) 
Check the durations for CD4 - they differ slightly on some tracks. 

Discogs can be very useful for documenting exactly what version of what track is on compilation CDs. Even with a reputable label such as Rhino, compilations can have alternate versions, radio edits, and all sorts of other 'surprise' versions (especially for 'fringe' music like Punk, but probably all sorts of others too). Less reputable record labels (such as Celoparta) sometimes cannot even spell their own name right, and regularly get the entire song title or artist name wrong on their compilation CD's. 

 The track durations given by **dcd** are expressed in minutes and seconds, and are correctly rounded UP to the nearest full second, the same way that most CD players do it. 
Whereas **cdcd** shows durations in minutes:seconds:frames and it doesn't have an option to round up to full seconds.
I already have that capability with **cdparanoia**: it returns EXACTLY the same values as **cdcd** for every CD that I try.

I used to have an easy way of getting the track durations when contributing information to Discogs: an **rxvt** window set to Always On Top, and **dcd** output. 
I even posted in some of the Discogs forums, suggesting that other Discogs users try Ubuntu (with dcd and their favourite web browesr) for easy duration copy/paste. 

So, how does one go about installing **dcd** on Ubuntu 10.x?

---

