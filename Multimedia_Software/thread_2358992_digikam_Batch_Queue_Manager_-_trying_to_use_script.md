---
title: "digikam Batch Queue Manager - trying to use script: can't make it work"
date: 2017-04-19
forum: Multimedia Software
---

### Post by pizzipie on 2017-04-19
Hi,

I just installed Digikam v5.5.0 on Ubuntu MATE 16.04. I am new to Digikam so just learning. I can't get the script to run properly. 

I am trying to move processed pictures from the Digikam Album Directory to another directory.

Here is my script* move-digikam-photos.sh*: 

**rsync -avz  /home/polly/VB-share/processedFiles  /home/polly/digikam-receiving** (works fine in the terminal)

[ATTACH=CONFIG]274659[/ATTACH]
I don't follow what the above instructions in the attachment mean. Hope someone can help decipher that for me.
I tried putting name of the script and then the CODE above into the shell script window with no success ( files don't get moved).

In the digikam Settings=>Configure Notification window I have checked off Batch Queue Completed and Show message boxes.
In the Run Command box I have inserted[B] /home/polly/move-digikam-photos.sh.

[/B]Thanks for any help you can give me on this issue,

R

---

