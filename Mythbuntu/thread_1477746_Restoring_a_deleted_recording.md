---
title: "Restoring a deleted recording"
date: 2010-05-09
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-09
I have made a bit of a mess of one of my recordings, and would like to restore it from a backup.

I have a movie which I had tried to remove ads from by transcoding. This, my first attempt at doing so, turned it from a .mpg into a .nuv file. I thought this was OK, as the .nuv file played OK on my MythTV box, but I also often watch things via a media streamer in another room, which doesn't seem to be able to play .nuv files. It's fine with .mpgs. So I want to start again from the .mpg file, this time keeping it in .mpg format (I now know how to do that if the recording shows up in MythTV recordings).

So, I have the original .mpg file, but can't figure out how to get it back into my MythTV recordings. The database now thinks that the associated file is the .nuv file, and when I delete the .nuv file and put the .mpg file back in the recordings folder, it just tells me the file is not found.

I guess I could manually edit the MySQL database, right? But I'm a bit reluctant to do that as I guess it would be mightily easy to break things. Is there an alternative?

Just as another thought, I don't absolutely have to get it back into recordings. What I want to do is cut out the ads again, which is pretty easy to do from the MythTV front end once it's there as a recording. If there's another reasonable way to do that, that would be OK too.

Any thoughts?
Thanks
NM

---

### Post by ian dobson on 2010-05-09
Hi,

You'll need to manually edit your recordings table, change the basename (filename) field to point to the mpg file. Then run the mythcommflag job on the file to rebuild the skip list.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-10
Thanks for that, Ian.

Just to be sure, when you say "manually edit your recordings table", you're talking about rolling up my sleeves and delving into the MySQL database, right?

---

### Post by ian dobson on 2010-05-10
Hi,

Yes, if you've got apache/phpmyadmin installed on your backend just use that to modify the record in the recorded table to point to your old recording name.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-16
Thanks Ian, and thanks in particular for suggesting using PhPMyAdmin, which was an awful lot easier than it would have been had I tried typing SQL commands manually.

However, this has been only partially successful. The recording can now be found and played, but I can no longer rewind, fast forward, or edit out the adverts.

If I try to edit, it says "No seektable".

Does anyone know how I can fix this?

Thanks
NM

---

### Post by ian dobson on 2010-05-16
Hi,

Try running mythcommflag on the recording, that might recreate the seek table.

Have a look here [http://www.mythtv.org/wiki/Repairing_the_Seektable](http://www.mythtv.org/wiki/Repairing_the_Seektable)

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-16
Thanks, that worked.

Well, sort of.

I tried running mythcommflag from the MythTV front end, and that didn't work. However, when I checked the myth-backend log file, it told me what the problem was and what options to use with the mythcommflag command (there was a --rebuild in there somewhere).

So then, all I had to do was copy the suggested syntax from the log file and run it at a shell prompt. Then it worked as desired.

---

