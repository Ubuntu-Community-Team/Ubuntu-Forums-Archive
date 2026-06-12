---
title: "MythTV Gallery - how to change columns / rows"
date: 2009-07-26
forum: Mythbuntu
---

### Post by usererror on 2009-07-26
How do I change the number of columns wide my view is of my pictures is in MythTV Gallery?  right now I have 15 folders and it does 6 or 8 columns on each display, and they are off the screen so i can't see them.

i cannot find it in the setup. It appears to not be theme based either...because it happens on all themes.

Thanks!

---

### Post by chipppy on 2009-07-27
Good Afternoon

I think the more important questions is
Why are the columns off the edge of the screen?

Personally I would be looking into the screen borders which is a question that appears every now and then.  Try resizing you screen (Utilities/Setup ==> Setup ==>Gerneal ==> Screen Appearance) I think.

Baring that look around 
Utilities/Setup ==> Setup ==>Gerneal ==> Images (i think).  i will have a look tonight once the kids are in bed.

Cheers
chipppy

---

### Post by usererror on 2009-07-27
> **chipppy said:**
> Good Afternoon

I think the more important questions is
Why are the columns off the edge of the screen?

Personally I would be looking into the screen borders which is a question that appears every now and then.  Try resizing you screen (Utilities/Setup ==> Setup ==>Gerneal ==> Screen Appearance) I think.

Baring that look around 
Utilities/Setup ==> Setup ==>Gerneal ==> Images (i think).  i will have a look tonight once the kids are in bed.

Cheers
chipppy

Thanks for helping out. I don't think the screen borders are the problem, because everything else displays perfectly, nothing else is off the edge of the screen. I did go to the settings for Images under the main setup menu in myth, but it had no options for changing the columns for images.

to be sure though I'll check the border settings when I return home tonight.

---

### Post by bcg30506 on 2009-07-27
I have this same issue using the Mythbuntu-wide theme.  It works fine with the Minimalist-wide theme.

---

### Post by usererror on 2009-07-27
> **bcg30506 said:**
> I have this same issue using the Mythbuntu-wide theme.  It works fine with the Minimalist-wide theme.

I will have to try that theme when i get home. Thanks.  I am currently using the Mythbuntu-wide theme as well!

---

### Post by crez79 on 2009-07-28
Same problem [here]("http://ubuntuforums.org/showthread.php?p=7299704"). Try adjusting the "blackhole."

I made these changes:
```

<container name="view">
      <area>330,77,930,620</area>                      #<-------620

      <blackhole name="view" draworder="0">
            <area>0,0,840,500</area>                     #<---------500
      </blackhole>
      <image name="scrollUpReg" draworder="0" fleximage="no">
        <context>0</context>
        <filename>shared/uparrow.png</filename>
        <position>950,490</position>
      </image>
      
      <textarea name="help1" draworder="1">
        <area>0,530,200,35</area>                       #<----------- 530
        <font>info</font>
        <value>SELECT: View</value>
      </textarea>

      <textarea name="help2" draworder="1">
        <area>225,530,325,35</area>                   #<-------------530
        <font>info</font>
        <value>MENU: Activate Menu</value>
      </textarea>
```These changes were made to  /usr/share/mythtv/themes/glass-wide/gallery-ui.xml for me because I am using the glass-wide theme. I am using 1920x1080 resolution. You don't need to restart mythfrontend or anything, I just sshed in and edited the file, saved it and opened mythgallery. If it didn't work, exit mythgallery, mess around a little more, save it, the open mythgallery to see the changes.

---

### Post by usererror on 2009-07-28
crez79,

THANK YOU!  I also switched to Glass-Wide and like it much better.  Since our resolutions are exactly the same I used the same modifications to the gallery-ui.xml file. VNC'd into the box and the gallery works great now.  Thanks a lot.

What exactly does "black hole" do in the UI? Do you know?

---

### Post by crez79 on 2009-07-28
I think it is the place that the content is diaplayed. In this case the pictures. That is just a guess, but it seems to be the case, at least with mythgallery.

---

### Post by bcg30506 on 2009-07-28
Thanks!  I too changed to the glass-wide theme and applied your change to the gallery-ui.xml file and it works for me.  It'd be nice to understand the relationship of all those numbers so all the themes can be fixed for the image thumbnails.

---

### Post by crez79 on 2009-07-28
I think it goes "x,y,x length,y length" in pixels so that (x,y) is the top left corner, and (x+x-length,y+y length) is the lower right corner. Somehow magically it proportions those points for different resolutions.  I am not sure of how all that works.

I think the view container is the viewable portion and the blackhole is where the content is.

There is a guide [here]("http://www.mythtv.org/wiki/Theme_development_guide") but it is too complex for me.

---

### Post by bcg30506 on 2009-07-29
The one issue I have with glass-wide theme is you cannot make DVDs with MythArchive.  There are no buttons for Add Recording, etc.

So I switched to Mythbuntu 7.10 theme and it all seems to work.

---

### Post by williammanda on 2009-09-09
I played around with the previous suggestion but ended up making only this change in bold in /usr/share/mythtv/themes/Mythbuntu-8.04-wide/gallery-ui.xml:

```
   </container>

      <container name="view">
      <area>330,87,930,620</area>

      <blackhole name="view" draworder="0">
            <area>0,0,**900,480**</area>    (this was 1240,620)
      </blackhole>
```

My video display is 1366 x 768. This gives me an array of 6 x 3 (6 wide by 3 tall) photos. Previously It was displaying 8 x 4. Two pictures were lost on the right of the screen and a fourth row over wrote the commands on the bottom of the screen.
Thanks

---

