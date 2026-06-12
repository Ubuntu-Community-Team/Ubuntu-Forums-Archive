---
title: "trouble playing files in vlc through terminal"
date: 2013-04-17
forum: Multimedia Software
---

### Post by adarshraghu on 2013-04-17
i am trying to open video files through vlc i used the following command

[B][I]adarsh@ubuntu:/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip$ vlc Inglourious Basterds.mp4
[/I][/B]
it opens vlc but nothing plays and a vlc error window opens with this message :

 [B][I][COLOR=#ff0000]File reading failed:[/COLOR]
[/I][/B]
***[COLOR=#000000]VLC could not open the file "/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious". (No such file or directory)[/COLOR]***
***[COLOR=#ff0000]Your input can't be opened:[/COLOR]***
***[COLOR=#000000]VLC is unable to open the MRL 'file:///media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious'. Check the log for details.[/COLOR]***
***[COLOR=#ff0000]File reading failed:[/COLOR]***
***[COLOR=#000000]VLC could not open the file "/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Basterds.mp4". (No such file or directory)[/COLOR]***
***[COLOR=#ff0000]Your input can't be opened:[/COLOR]***
[B][I][COLOR=#000000]VLC is unable to open the MRL 'file:///media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Basterds.mp4'. Check the log for details.


[/COLOR][/I][/B][COLOR=#000000]the following errors are also displayed in the terminal screen :

[I][B]VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x905b188] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb0800bc8] filesystem access error: cannot open file /media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious (No such file or directory)
[0xb5300618] main input error: open of `file:///media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious' failed
[0xb08011e8] filesystem access error: cannot open file /media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Basterds.mp4 (No such file or directory)
[0xb5303a60] main input error: open of `file:///media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Basterds.mp4' failed
adarsh@ubuntu:/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip$ vlc Inglourious Basterds.mp4
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x88c9188] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb0900bc8] filesystem access error: cannot open file /media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious (No such file or directory)
[0xb5400618] main input error: open of `file:///media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious' failed
[0xb09011e8] filesystem access error: cannot open file /media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Basterds.mp4 (No such file or directory)
[0xb5403a60] main input error: open of `file:///media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Basterds.mp4' failed

[/B][/I][/COLOR]
[COLOR=#000000]any help will be appreciated thanx in advance



[/COLOR]

---

### Post by sanderj on 2013-04-17
spaces!!!

Solutions:

1) double quotes around the filename
2) \ before space
3) type "vlc Ing" (without quotes), and press TAB

---

### Post by ajgreeny on 2013-04-17
There are also some variations in your spelling which might be adding to your problems, even after you use the double quotes or escape marks in the file name.

The simplest way with such names, ie long names or those including spaces is to use tab completion by starting to type the name and then hitting tab.

---

### Post by prshah on 2013-04-17
> **adarshraghu said:**
> [B][I]adarsh@ubuntu:/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip$ vlc Inglourious Basterds.mp4
[/I][/B]
it opens vlc but nothing plays and a vlc error window opens with this message :

 [B][I][COLOR=#ff0000]File reading failed:[/COLOR]
[/I][/B]
***[COLOR=#000000]VLC could not open the file "/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/Inglourious". (No such file or directory)[/COLOR]***


The file name contains a space, either enclose it in quote or escape the special charaters, eg```

vlc "file with space.mp4" #or
vlc file\ with\ space.mp4
```

Adding a "\" before a special charater such as a space or quotation marks tells the system to take the following character literally, and not process it.

---

### Post by shantiq on 2013-04-18
cd to folder where file is


```
cd   [COLOR=#000000]/media/adarsh/movies/IngloriousBastards_720P_H264_BDRip/     &&  vlc *         
[/COLOR]
```[COLOR=#000000]

or  if your file has spaces or is really long find a **unique part** of the name and run that between **

example:

i have a file named   [/COLOR]> World_Routes_-_A_Night_Out_in_Joliette_b01bzqq6_default.flv  in my Music folder   so



```
cd Music && vlc *oliette*
```       will start it



**=======================**

another way:

run   ```
 find|grep -i [COLOR=#000000]Inglourious[/COLOR]
```       and copy the line where you see your file 

```
 vlc  "lineyoufoundyourfileon"
```      "" only needed if there are gaps in the line

---

### Post by anandu on 2013-04-18
Either use Tab to show the full file name or go to the movie directory and type command "vlc *"


Anandu
[www.ananduvr.com](www.ananduvr.com)

---

