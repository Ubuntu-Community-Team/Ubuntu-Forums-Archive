---
title: "Brasero &amp; .nrg files"
date: 2009-07-05
forum: Multimedia Software
---

### Post by radtek on 2009-07-05
Can Brasero burn or convert .nrg files?

If not is there a working program that does?

---

### Post by frenkel on 2009-07-05
Did you even search google or this forum?
First hit was this: [https://answers.launchpad.net/ubuntu/+question/5979]("https://answers.launchpad.net/ubuntu/+question/5979")

---

### Post by radtek on 2009-07-05
Nice thread there...

I had already done some research on the nrg2iso & nrg4iso and they seem problematical. Anyway I get this:

```
radtek@tosh:~$ nrg2iso gm1.nrg gm1.iso
It seems that gm1.nrg is already an ISO 9660 image 
[Aborting conversion]
radtek@tosh:~$ 

```
And here's a snippet of the return when I ran this command:

```
radtek@tosh:~$ od -Ad -c gm1.nrg | more
0000000  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
*
0032768 001   C   D   0   0   1 001  \0                                
0032784                                                                
0032800                                   G   R   I   M   _   D   I   S
0032816   K   _   A                                                    
0032832                                  \0  \0  \0  \0  \0  \0  \0  \0
0032848   C 354 004  \0  \0 004 354   C  \0  \0  \0  \0  \0  \0  \0  \0
0032864  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
0032880  \0  \0  \0  \0  \0  \0  \0  \0 001  \0  \0 001 001  \0  \0 001
0032896  \0  \b  \b  \0   V  \0  \0  \0  \0  \0  \0   V 035  \0  \0  \0
0032912  \0  \0  \0  \0  \0  \0  \0 036  \0  \0  \0  \0   "  \0 022  \0
0032928  \0  \0  \0  \0  \0 022  \0  \b  \0  \0  \0  \0  \b  \0   e  \n
0032944 032 023   5  \0 344 002  \0  \0 001  \0  \0 001 001  \0        
0032960                                                                
*
0033328                                                           N   E
0033344   R   O       -       B   U   R   N   I   N   G       R   O   M
0033360                                                                
*

```

Still can Brasero do this natively and/or is there a plugin?

I haven't delved into this *completely* and am wondering if this is a complete waste of time. I can probably find .iso's of what I want in a torrent but that would be giving up too soon LOL...

---

