---
title: "Need music [mp3] auto tagger and file renamer"
date: 2008-07-03
forum: Multimedia Software
---

### Post by TusharG on 2008-07-03
This is my one more attempt to move to Linux... I've patience and I've given many tries time to time....

I've creative zen mp3 player and usually i sync it with my hdd drive. I use creative software and maintain exclusive directory structure on zen player for music of various languages and tempo like: New Hindi, Old Hindi, English, Marathi, Classical, Vocal
I use winamp to tag the mp3 files and in 90% of the time when I ask winamp to auto tag the file it works. Later on I use another tool to rename the file as "<Artist> - <Track Name>"

I'd like to make thing work exactly the same way... I'm now using latest GNomad2 which now without crashing is able to transfer my files from Zen to HDD but by distroying the entire directory structure. I'm ok with the same... However I need a way to autotag the mp3 files. So far I've tried 3 tools and all them fail.
1. easytag - lacks the auto tagging and music ID3 tag guessing that winamp provides
2. tagtool - does not provide auto tagging of files and tag guessing
3. cowbell - does not provide auto tagging of files and tag guessing
4. Amarok & Rhythumbox - has only manual tagging facility
5. Picard - Tag guess is very poor
6. Jaikoz - is a paid tool

Equally I need a tool to rename files based on ID3 tag.

Can anyone suggest some good tools to do the same? i.e to autotag files and renames files based on the ID3 info.

---

### Post by TusharG on 2008-07-03
Can anyone help?
I also tried running winamp in wine but no success. Winamp runs in wine but if I try to update the tags via wine it just hangs.

---

### Post by Roinator on 2008-07-24
pyRenamer can rename files based on ID3.  For auto tagging I use picard.  It really is the best one and you can set it to automatically structure your tagged files.  Thats how I have mine set up :)

---

### Post by Gadgetech on 2008-08-13
You can use EasyTAG to do what you describe.  To auto fill the tags, do the following:
[LIST=1]
[*]Open EasyTAG and navigate to the album folder which contains the files you want to edit.
[*]Click the blue box icon to select all files.
[*]Click the CD icon for Search CDDB.
[*]Click on Find in the window that comes up.
[*]Select the correct album from the search results.
[*]Click the blue Select All icon.
[*]Click the Apply button.
[*]Click the Close button
[*]Click on the Save Files icon.
[*]Click Yes on the confirmation prompts
[/LIST]

Now, to do the file renaming:
[LIST=1]
[*]Make sure all your files are selected.
[*]Click on the green Scan Files icon.
[*]In the new window, select Rename File and Directory in the scanner drop down list.
[*]Set the rename field to show  %a - %t
[*]Click the green icon next to the scanner drop down.
[*]Click on the Exit icon.
[*]Click on the Save Files icon.
[*]Click Yes on the confirmation prompts
[/LIST]

---

### Post by Pifilatakanemu on 2009-10-29
hey there,
i Know this is quite an old thread, but i wanted to come back to the first question.
i want to autotag my collection. i'm trying picard RIGHT now , but the mass of media files makes it to blow up to 1,5gig of memory-use. this doesn't really make it handable. 
i can try to do this step by step with parts of my collection, but i would like to know if there is another option.

@Gadetech: you're proposal includes quite a lot of manual steps.. it's not really "auto".. ;)

---

### Post by Polish Rifle on 2011-02-23
Tried EasyTag and I was very disappointed with the search results.  It's nearly impossible for it to tag a mix or playlist.

---

### Post by ram130 on 2011-08-08
> **Polish Rifle said:**
> Tried EasyTag and I was very disappointed with the search results.  It's nearly impossible for it to tag a mix or playlist.

So any suggestions for a mix or playlist with different files?

---

