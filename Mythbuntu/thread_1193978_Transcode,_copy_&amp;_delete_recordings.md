---
title: "Transcode, copy &amp; delete recordings ?"
date: 2009-06-22
forum: Mythbuntu
---

### Post by laffinet on 2009-06-22
Hi !

For certain recordings (to be defined when scheduling the recording) I would like the following to occur automatically:

(0. Delete the commercials)
1. Transcode the recording into a useful format (like avi or mpg)
2. copy the resulting file into a directory of my choice (say /home/username/videos), with a useful filename (like Show-Episode or something like that)
3. Delete the original recording file

(Not sure about step 0. since commercial flagging isn't 100% and I don't want to accidentally delete part of a show)

From what I can tell this should be possible by doing the following:

a. schedule the recording with the option to automatically run transcoding on "autodetect" (as quality setting)
b. setting up a separate user job like so:
```
cp "%DIR%/%FILE%" "/home/username/videos/%TITLE% - %SUBTITLE% - %STARTTIME%.mpg"
```
c. include the user job in the recording options (similar to a.) when scheduling the recording

Which leaves deleting the original recording. Can anyone tell me how to do this ?

Also, is what I'm planning to do going to work ? If not, any other suggestions ?

Cheers.

---

### Post by newlinux on 2009-06-22
There is a transcode setting that that tells gives it the option of deleting the original recording file after transcoding. Not sure off the top of my head where this setting. Not the transcoded file will still be in the recordings directory (and in the recordings listing), but the original recording will be gone.

---

