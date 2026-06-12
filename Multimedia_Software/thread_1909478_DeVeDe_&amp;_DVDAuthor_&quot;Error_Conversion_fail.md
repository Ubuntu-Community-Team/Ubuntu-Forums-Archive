---
title: "DeVeDe &amp; DVDAuthor &quot;Error: Conversion failed. It seems a bug of SPUMUX&quot; (sic)"
date: 2012-01-15
forum: Multimedia Software
---

### Post by rocksockdoc on 2012-01-15
Using DeVeDe, I was authoring overnight the longest ISO I've ever done (about 8 hours) using a mix of AVI and MP4 files (with subtitle .srt files).

In the morning, this error awaited me:
**"Error: Conversion failed. It seems** [to be][B] a bug of SPUMUX" 

[/B] Googling, it seems to be a dvdauthor error message, and it seems to be in regards to subtitles.

It's no big deal but I wonder if anyone knows how to debug further (there is no log file that I know of that was produced).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210906&stc=1&d=1326644975[/IMG]

---

### Post by rocksockdoc on 2012-01-15
Digging further,[ this]("http://ubuntuforums.org/showpost.php?p=9515203&postcount=17") seems to be one of the better potential explanations:
[ubuntu] [Creating a DVD from .avi files]("http://ubuntuforums.org/showthread.php?t=796151") - 

The spumux error is specifically discussed in the red**[COLOR=DarkRed] section 2.3.5.1.1[/COLOR]** below.

> **emperillado said:**
> 
First than all I expended many days trying to figure out how to create  movies out of any format, not only .avi but all the formats you get them  from Internet and found that DeVeDe is a great tool to do it. It works  fine with all the formats I have tried until now.

I'm using Ubuntu 10.04 LTS, but this should work just fine for every version.

This is what you have to do in order to make it work, and I'm going to  start from scratch because I want this guide to be useful even for the  1st time users:

 1 Make sure that you already have installed DeVeDe. To do that just go  to Applications>Sound & Video and look for DeVeDe DVD/CD Video  Creator. If you don't have it then this is what you have to do in order  to install it:[INDENT]  1.1 Go to Applications>Ubuntu Software Center
 1.2 Type &#8220;devede&#8221; without the quotation marks on the search field at  the top-right corner where the binoculars are and press Enter.
 1.3 You should get at least one item in the results list which is  DeVeDe and it has a &#8220;Install&#8221; button so click it and wait for the  program to be installed. And that's it, you already have DeVeDe on your  ubuntu.
[/INDENT]2 Go to Applications>Sound & Video>DeVeDe DVD/CD Video Creator. This opens DeVeDe.[INDENT]  2.1 Here you are going to get a simple menu called &#8220;Disk type selection&#8221;, choose the first option &#8220;Video DVD&#8221;.
 2.2 Now you get the &#8220;Unsaved disc structure &#8211; DeVeDe&#8221; window, it is  divided in several sections: Titles, Files, File info, Disk usage,  Default format, and Menus. Now under Titles click &#8220;Properties&#8221; and  change &#8220;Title 1&#8221; for the name of your movie, also choose &#8220;Play the first  title&#8221; and hit OK.
 2.3 Under &#8220;Files&#8221; click &#8220;Add&#8221; button. You will get the &#8220;File properties&#8221; window:[INDENT]  2.3.1 Under &#8220;File&#8221; click the little folder icon on the right.
 2.3.2 Browse to the folder your movie is and select it. If the format  is supported it is going to show the file on the list. Click &#8220;Open&#8221;
 2.3.3 You are back to the &#8220;File properties&#8221; window.
 2.3.4 Under &#8220;Video format&#8221; choose &#8220;PAL/SECAM&#8221; if you are in Europe or &#8220;NTSC&#8221; for USA.
 2.3.5 Now under &#8220;Subtitles&#8221; click &#8220;Add&#8221;. You are going to get the &#8220;devede&#8221; window:[INDENT]  2.3.5.1 Hit the little folder icon at the right of the &#8220;File&#8221; field and browse for your subtitle file.[INDENT]  [COLOR=DarkRed]**2.3.5.1.1 WARNING: Over here is where everybody gets stuck:**[/COLOR][INDENT][COLOR=DarkRed][B]   2.3.5.1.1.1 First than anything, the fact that DeVeDe is showing a  file doesn't mean that it is a subtitle file!!! Choose carefully. DeVeDe  supports .sub, .srt, .ssa, .smi, .txt, .aqt, .jss and .a s s, but you can  trick the program choosing for example a .txt with no subtitles at all,  the program takes it but you are going to get the &#8220;Conversion failed it  seems a bug of SPUMUX&#8221;. It also happened to me with a .nfo and a .sfv  files that I selected by error.
 2.3.5.1.1.2 DeVeDe tries to detect if the file is pure ASCII, UTF-8 or  UTF-16; in case it's unable to do so, it will set the last format  selected, so if the detection doesn't work and you don't choose the  proper format for the codepage you are going to get an error. I always  try to use .srt and .sub and never have problems with them.
[/B][/COLOR] [/INDENT][/INDENT][COLOR=DarkRed][B]2.3.5.2 Once you have chosen you subtitle file  you must choose the language too. This allows the DVD player to show  the language code when you enable the subtitles.
 2.3.5.3 Hit OK.
[/B][/COLOR] [/INDENT][COLOR=DarkRed]**2.3.6 Now click on &#8220;Preview&#8221;. This is really important  because if you get any errors over here it means that you are not going  to be able to create the .iso file at all.**[/COLOR][INDENT][COLOR=DarkRed][B]  2.3.6.1 If you  get errors in the preview phase, try removing the subtitle files one by  one until you don't get errors. If you are using only one subtitle file  and you are sure that this file is not corrupted then try changing the  encoding, but, the list is really big. I would rather download a new  subtitles file from internet.
 2.3.6.2 Now, if you were able to preview the title and only in that case, click OK.[/B][/COLOR]
[/INDENT][/INDENT]2.4 You are back to the &#8220;Unsaved disc structure&#8221; window:[INDENT]   2.4.1 Under &#8220;Disc usage&#8221; click &#8220;Adjust disc usage&#8221;. Clicking on it  will adjust the video rate in each video in order to use the 100% of the  disk. To do so, DeVeDe takes in account the final resolution and the  length, giving more bits per second to the videos with a higher  resolution, but always in a proportional way. Remember that you should  always click again the Adjust disk usage button after changing the final  resolution, adding or removing subtitles, adding or removing titles,  or, in general, before creating your disk, in order to assign a good  video bit rate to each film. Remember that changing the soundtrack used  in the menus will change the disk usage too. (Taken from DeVeDe help  pages).
 2.4.2 Under &#8220;Default format&#8221; make sure that you have chosen the right format for your country.
 2.4.3 Under &#8220;Menus&#8221; make sure that &#8220;Create a menu with the titles&#8221; is checked.
 2.4.4 You don't really need to mess up with the &#8220;Advanced options&#8221;, they are nice but the default values work just fine.
 2.4.5 Click &#8220;Forward&#8221;.
 2.4.6 You get a little window that allows you to name the .iso file to  be created, it is advisable to change the word &#8220;movie&#8221; for the name of  the movie. I also prefer to change the folder because by default it  drops the .iso files on a folder on the &#8220;Home&#8221; folder and it rapidly  becomes too crowded. 
 2.4.7 Now click OK. The program starts the creation of the .iso file.  It takes a long time to do it, just like any other similar program, it  depends on your computer speed obviously, but any ways it is going to  take some time. When it finishes you are going to end up with a .iso  file ready to burn a DVD.
[/INDENT][/INDENT]3 Now go to the folder where the .iso file was  created. It is going to be either &#8220;Home/movie&#8221; or the one that you  chosen on step 2.4.6.[INDENT]  3.1 Right-click the .iso file that DeVeDe just created.
 3.2 Click &#8220;Write to Disc...&#8221;. You get the &#8220;Write to Disk&#8221; window:[INDENT]   3.2.1 Under &#8220;Select a disc to write to&#8221; make sure that you it shows  your DVD writer and don't pay to much attention to the size of the file.
 3.2.2 Click on &#8220;Properties&#8221;[INDENT]  3.2.2.1 Under &#8220;Burning speed&#8221;  choose the lowest possible value, normally it is 4x. This makes the DVD a  lot more compatible with old DVD players.
 3.2.2.2 Click &#8220;Close&#8221;
[/INDENT]3.2.3 Click either &#8220;Burn Several Copies&#8221; or &#8220;Burn&#8221; depending on your own needs.
[/INDENT]3.3 Now you are going to create a DVD. The creation is a  very fast process even at the lowest speed. It should be something  around 5 minutes.[/INDENT]

---

