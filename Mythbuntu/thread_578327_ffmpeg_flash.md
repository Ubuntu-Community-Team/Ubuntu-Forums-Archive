---
title: "ffmpeg flash"
date: 2007-10-17
forum: Mythbuntu
---

### Post by kingmoffa on 2007-10-17
Hi , does mythbuntu come with a version of ffmpeg that supports flash?

I've been trying to setup on the fly flash encoding
([http://knoppmythwiki.org/index.php?page=MythwebFlash](http://knoppmythwiki.org/index.php?page=MythwebFlash)) 
 using my standard ubuntu feisty mythbackend installation.I think the problems I have are becuase the ffmpeg with feisty doesn't support flash (swf) encoding.

---

### Post by superm1 on 2007-10-17
Your best bet is to enable medibuntu (See mythbuntu control centre's codecs tab).  From there you can activate their build of flash.

---

### Post by kingmoffa on 2007-10-24
Thanks for the advice , but no joy.
```

From aptitude:
ffmpeg - multimedia player, server and encoder - Medibuntu package                                                                                                    

This package contains the ffplay multimedia player, the ffserver streaming server and the ffmpeg audio and video encoder. They support most existing file   
formats (AVI, MPEG, OGG, Matroska, ASF...) and encoding formats (MPEG, DivX, MPEG4, AC3, DV...).                                                            
                                                                                                                                                            
This package is built with the "risky" option, to enable mp3/mp4/h264/amr support. Therefore, it is in Medibuntu as it might violate patents.               
                                                                                                                                                           
This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!  


```

Does anyone know any other repositories where ffmpeg with swf / flash are enabled?

---

