---
title: "MP3 Tag Editor: fill tag info from file name"
date: 2009-03-09
forum: Multimedia Software
---

### Post by UranUtan on 2009-03-09
Hi,

Under Windows, I used MP3Tag [http://www.mp3tag.de/en/](http://www.mp3tag.de/en/) which allows me to do a lot of tag editing. It can do rename a file from tags and also extract tag from file name.

I have installed EasyTag, and I can't figure out how to extract a tag info from a file name. Example: the file name pattern is :

12. Artist name - Title.mp3

I would like to extract from the file name and populate the ID3Tag from the extracted info: Track number, Artist, Tilte.

Is there a tag editor working under Linux which allow to do so?

Thanks in advance for any help.

---

### Post by dartmusic on 2009-03-10
Look in the repos for Easy Tag.  If you have ANY m4a or aac files, you'll need to get the version called easytag-aac.

It's a little slow and the GUI is a little buggy, but there are many different ways to auto tag your files and batch editing is fairly simple.

Good luck.

---

### Post by UranUtan on 2009-03-10
Hi,

Thanks for your help. I have already installed EasyTag as mentioned in 1st post.

What I wanted to do is to fill missing tag (the track info) from the file name. Can you show me how to parse the file name to extract and fill the Track info?

Thanks

---

### Post by dartmusic on 2009-03-10
Sure...

Open EasyTag, navigate to a folder with music files in it, select all the files in the folder, or all the files you want to tag, click on the "Scan Files" button (you'll have to hover over them to figure out which one it is).

Then, make sure the scanner dropdown is set to "Fill Tag," then in the Fill Tag field, make the appropriate edits until the example below the field looks like what you're looking for.  If you need further help as to what to put in the Fill Tag field, click on the "?" button for the legend (listing of what the different possible codes are to translate with) and hit the mask button to list some starting points.  

When you're happy with the results, click the "Scan Files" button (in the Scan Files dialog box, not the one you originally clicked to get where you are...the icons look the same) and your changes will be applied.  If you are not getting Artist or Album name, simply select all that you want to change, enter the data and click the little button next to that field and all files that are selected will the filled in or changed to that artist or album.  This works in most fields.  

When you're done, click the save button and you're done.

Let me know if you have any other questions.

::r

PS:  The CDDB scanner often works pretty well, if you have full albums that you're trying to tag, or at least commercially available song files.

PPS:  I am apparently half awake still.  According to what you wrote in your original post, try this in the Fill Tag field:

%n. %a - %t

Let me know how you make out.

---

