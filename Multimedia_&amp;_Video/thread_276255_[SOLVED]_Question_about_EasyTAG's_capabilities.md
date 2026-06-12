---
title: "[SOLVED] Question about EasyTAG's capabilities"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by bswilson on 2006-10-12
Friends,

I have a question about using **EasyTAG**, and I've not been able to find an answer in any documentation or Internet resources.

One feature that I really enjoyed from **iTunes** was the ability to edit a file's tag to change the album name and have **iTunes** automatically create a directory for the album name, then move the file to that location. When I browsed my directories of music, everything would be perfectly organized by Artist, then Album, then Song Title.

I now lament the lack of my **EasyTAG** + **Rhythmbox** combination on Ubuntu's ability to do this.

My question really is, can this be done?  Is there some kind of configuration in **EasyTAG** that I can set to facilitate the behavior I'm describing?  Is there another tool that might do this for me?

---

### Post by sp4rd on 2006-10-13
EasyTAG can do this.  I've done it with mp3 files.  I don't know if the version in ubuntu supports m4a/aac tags, so the following steps relate to mp3 files with ID3 tags.  The following steps should work if all of your music files are in one directory and have their tags filled in.  You might want to create a test directory first and throw some random music files in it just to experiment with so you don't lose anything.

1. Make sure your tag fields for Title, Artist and Album are filled in.  If not, fill them in and save them.

2. Next we're going to use the 'Scanner' menu option to create the directories and have the files moved into the newly created subdirectories.  This will move all the files into the newly created subdirectories(not copy them) so if something goes amiss your files may end up someplace else and not where you would expect them.  Try my suggestion of a test case first, see above.

3. Once you've selected the files, the selected files should be highlighted, choose the 'Scanner->Rename File(s) and Directory...' menu option from the top menu.  This will open Scanners 'Tag and File name scan' box with the 'Rename File and Directories' option chosen.  If you want to see the Legend for the tag variables click on the `?` Show/Hide Legend button.

4. Input your tag variables.  For EasyTAG to create subdirectories insert a "/" between the tag variables.  As an example this is what my Scanners 'Rename File and Directory' input would look like if I have a whole bunch of mp3 files in one directory and I wanted to move them into subdirectories based on Artist/Album/TrackNumber - Songname

Rename File and Directory

%a/%b/%n - %t

then click on the little green scanner icon "Open Scanner window/Scan selected files" next to "Rename File and Directories".

5. If the files you were working of become unselected Select them again.  (I usually do all of them in one go So I would select the dark blue 'Select All Files' icon).  

6. Finally select "Save File(s)", looks like a disk icon.  That should move all your selected files in the working directory into their own directory structure based on the above tag structure. EasyTAG will pop a confirmation box asking you "Do you want to write the tag of file 'blahblah.mp3'?" If you want to let EasyTAG do them all also select "Repeat action for the rest of the files".  Do the same for "Do you want to rename the directory.  Look at the 'to' destination directory if it's not what you expect click "Cancel" else click "Yes".

7. If every thing went right you should see newly created directories in the working directory starting with the Artist name

8. Pat yourself on the back.

---

### Post by bswilson on 2006-10-13
Your explanation of the **Scanner** utility helped me greatly, and you're right; **EasyTAG** does exactly what I want it to do in terms of renaming the directories.  *Thank you so much!* :) 

I followed your procedure, and noticed 1 strange behavior.  **EasyTAG** did rename all the directories via the **Scanner**, but in the **EasyTAG** window pane on the left (that shows the directory structure), I can't get that view to refresh and show me the newly created folders.  When I browse to that location the directories _are_ there.  Maybe that's a bug?  

In any case, than you very much for your help, and for your thorough post.

---

