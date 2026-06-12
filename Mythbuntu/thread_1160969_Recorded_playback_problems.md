---
title: "Recorded playback problems"
date: 2009-05-16
forum: Mythbuntu
---

### Post by TheConsultant on 2009-05-16
Hi @all,

if I had applied the latest dist-upgrade patches, I have problems with the playback in mythbuntu.
Playback is ok but when the commercial should automacally skipping, the playback ends. If I'm pressing the buttons picture down, only the timeline is jumping to the end. Pressing 'E' also appears a message "not searchable".
What can I do to fix this?
By the way. In another media playern, all work fine i.e. windows media player over samba.
Best regards
Martin

---

### Post by klc5555 on 2009-05-16
> **TheConsultant said:**
> Hi @all,

if I had applied the latest dist-upgrade patches, I have problems with the playback in mythbuntu.
Playback is ok but when the commercial should automacally skipping, the playback ends. If I'm pressing the buttons picture down, only the timeline is jumping to the end. Pressing 'E' also appears a message "not searchable".
What can I do to fix this?
By the way. In another media playern, all work fine i.e. windows media player over samba.
Best regards
Martin

Probably the seektable crashed in your mythconverg database. Happens frequently. Running the optimize_mythdb.pl script, which you can do from the "advanced" page in the mythbuntu control center (utilities/setup > setup > mythbuntu > advanced) usually takes care of most of it.

Sometimes an individual analog recording will require additional attention with mythcommflag, or a digital recording will with mythtranscode. The details are covered in the wiki page here: [http://www.mythtv.org/wiki/Repairing_the_Seektable](http://www.mythtv.org/wiki/Repairing_the_Seektable)

---

### Post by TheConsultant on 2009-05-16
Hi.
I don't think that it is mythcommflag, beacuse older reordings that succesfully played back before I have applied the latest patches are showing now the same behavior and they are sucessfully commflaged. Now I can't edit any record with 'e' (no searchable). I can't make five minute jumps forward, or back etc. pp. on all recordings. With other media players, this will working fine.
My impression is, that the internal player, or ffmpeg or so, are damaged or buggy.

I have tried the optimize table button - no effect!

Any further suggestions?

---

### Post by klc5555 on 2009-05-16
> **TheConsultant said:**
> Hi.
I don't think that it is mythcommflag, beacuse older reordings that succesfully played back before I have applied the latest patches are showing now the same behavior and they are sucessfully commflaged. Now I can't edit any record with 'e' (no searchable). I can't make five minute jumps forward, or back etc. pp. on all recordings. With other media players, this will working fine.
My impression is, that the internal player, or ffmpeg or so, are damaged or buggy.

I have tried the optimize table button - no effect!

Any further suggestions?

Like I said, it's the seektable. 

Mythcommflag does more than just commflag: it also builds seektables. So does mythtranscode.

Read and follow the instructions in the wiki page I linked to earlier.

[http://www.mythtv.org/wiki/Repairing_the_Seektable](http://www.mythtv.org/wiki/Repairing_the_Seektable)

You repaired the database sections with the optimize script, now use mythcommflag and mythtranscode to build your seektables the way the wiki page says to. 

mythcommflag --rebuild  will go through your entire database and rebuild all the seektables. Analog recordings will then be fine. The seektables for digital recordings, however, will still not be quite satisfactory after mythcommflag gets through with them, and will have to be done individually with:

mythtranscode --mpeg2 --buildindex -c -s

as the wiki guide says.

---

