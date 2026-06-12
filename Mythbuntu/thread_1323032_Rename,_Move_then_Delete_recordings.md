---
title: "Rename, Move then Delete recordings"
date: 2009-11-11
forum: Mythbuntu
---

### Post by prupert on 2009-11-11
Hi

I've done a fair bit of Googling, but no-one seems keen to do what I would like, so I thought I'd ask here (as I'm a mythbuntu user).

I use my mythbuntu box to record  TV programs, but as it is relatively weak power-wise, I use my Ubuntu server to convert all my recordings to MP4 and store them on a samba drive. Currently I have to use mythweb to manually move and rename each file (using the download link) and then delete them. 

I was thinking it would be super-cool if I could just create a script that did this for me each morning. 

I know I can use mythrename.pl to give me human-readable files, and to even create a symlink of the newly named file to somewhere else. However, I also want to then move that newly nicely named file to a mounted samba drive (which is on my server, which then runs a cron job on the folder each day to convert the files) and then delete the old file from the mythtv database and the recordings folder.

Some people have asked related questions here:
[http://www.gossamer-threads.com/lists/mythtv/users/296272?search_string=move%20recordings;#296272](http://www.gossamer-threads.com/lists/mythtv/users/296272?search_string=move%20recordings;#296272)
[http://ubuntuforums.org/showthread.php?t=432672](http://ubuntuforums.org/showthread.php?t=432672)

But in all cases, they wanted to keep the files within the mythtv database, whereas I want to delete them from the recordings database once they are moved.

The only way I can think of doing it is to write a script that each morning runs mythrename.pl, then to use find -exec and mv to find and copy all the .mpg files in the mythtv recordings folder to my samba folder and then call myth.find_orphans.pl to delete the orphaned DB entries.

However, this sounds like a really hacky way of doing it. Is there a better way, or is this the best of achieving what I want?

---

### Post by ian dobson on 2009-11-11
Hi,

Why not just use a perl script that searches the database for all files where the recording started yesterday, then copy them to your new source and then delete the rows from the recorded directory/recsearch table.

If you look on my website I have a simple perl script that checks the mythtv database structure.

Regards
Ian Dobson

---

### Post by prupert on 2009-11-11
Sadly I know nothing about perl, and I am only a begginer in Bash, so I wouldn't know where to start. I had a look at your script on your site, seems very in-depth, but then I wouldn't know how to modify it to suit my needs :(

---

### Post by laffinet on 2009-11-11
Ooops, just noticed that you want to do this from your ubuntu serverm not your mythbox, so nut sure if this is a suitable solution. Anyway, I typed it all now so here it is:

Search for mythnuv2mkv

It's a script that converts recordings to (for example) h264 mkv files (can use xvid etc. as well).
It also has an option to delete the original recording once converted, plus saving the converted file in a location of your choice.
If you set it up as a userjob and run it automatically after the recording is finished you should be able to achieve what you want. 
If you only want it to run at certain times you can restrict the times when user jobs can be run.

---

### Post by prupert on 2009-11-12
OOH, that might work, I could disable the transcoding part, but still use the deleting/moving function.

Thanks for the suggestion, I shall look into it.

Cheers

---

### Post by prupert on 2009-11-12
I actually ended up writing my own script (in Bash coz I don't know perl) that made use of mythrename.pl and myth.find_orphans.pl.

It is a bit of a hacky solution, but it seems to work. You can find the script and details of how I use it here:
[http://www.prupert.co.uk/2009/11/12/mythtv-recordings-rename-move-and-delete-from-the-database/](http://www.prupert.co.uk/2009/11/12/mythtv-recordings-rename-move-and-delete-from-the-database/)

---

