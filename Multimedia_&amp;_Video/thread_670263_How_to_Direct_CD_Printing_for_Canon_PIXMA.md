---
title: "How to: Direct CD Printing for Canon PIXMA"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by OzzyFrank on 2008-01-17
I've been looking for some decent software for printing directly to discs using the tray, and so far even the fairly crappy (yet functional) CD Label Print I got bundled with my Canon PIXMA MP800 looks a dream compared to the Linux alternatives (ie: NONE... and no, unfortunately it won't run under Wine). 

Anyway,** I have got a system working** so will supply as much info as I can.**[COLOR="Purple"] Please note this is for Canon PIXMA printers[/COLOR]**, but there should be plenty of info of interest to others, and could possibly be used with other printers (depending on tray size).

First off, if you haven't got**[COLOR="DarkRed"] gLabels[/COLOR]** installed do so. You can do it from Synaptic, but if you want to avoid the possibility of it crashing at a crucial point (outlined ahead, with a fix) you can download the latest (2.1.3-3) at [http://packages.debian.org/sid/glabels](http://packages.debian.org/sid/glabels) (get **glabels** and **glabels-data** and install them). However, I just thought I would see if I could get 2.1.3 working so you can just use Synaptic and follow my "fix" if you find gLabels also crashes on you when changing paper type to ***Other***.

OK, so you have gLabels installed, now download [http://www.ecis.com/~alizard/files/cd-print-canon-hub-templates.xml.zip](http://www.ecis.com/~alizard/files/cd-print-canon-hub-templates.xml.zip), unzip it, and put the xml file into** /usr/share/glabels/templates**.

When you open [COLOR="#8b0000"]**gLabels**[/COLOR] and choose **New**, pick ***Other*** for the paper type. If gLabels hangs for a sec then disappears, as happened with me and many other in forum posts, close it, open [COLOR="#8b0000"]**Configuration Editor**[/COLOR] (**gconf-editor**), then:

In the left-hand pane, select [COLOR="Blue"]**apps**[/COLOR], then **[COLOR="#0000ff"]glabels[/COLOR]**.
In the right-hand pane, select **[COLOR="#0000ff"]default-page-size[/COLOR]** and change the value from ***US-Letter*** to ***Other*** (just type over it).
Quit gconf-editor and start glabels.

You will see the default **Media Type** is now ***Other***, and in the drop-down list next to that will be **CanonPIXMA-directCD: Canon PIXMA direct CD printing**. Pick that and you will have a round work area with a cutout in the centre and it will print to the tray fine (make sure you pick the tray - I created a 2nd printer that is only the tray for this purpose, as many apps in Ubuntu let me choose the printer, but not the paper source).

So far, it seems better than I thought it would be. I imported one of my ready-to-go CD pics (a scan of a disc, cropped to that image with centre cut out), and these are quite large, so didn't expect it to fit without resizing. The pic started off as the small square I drew and when I reset it to its original size, I was pleasantly surprised to see it fit nicely into the work area, like I am used to with **CD Label Print**. I expected gLabels to be more like even MS Publisher, where I would have to downsize my pics to make them fit into the template.

So, I got more out of gLabels than I thought, but would still like to know of any apps that pop up made only for this task, especially as this only helps us Canon PIXMA owners. Also, I have no way of changing the size of the inner circle (the template is a bit conservative and I can get more print on my discs than it allows). And app made for printing onto discs would have to have this feature, and would be suited to more printers.

Hope this helps someone else, and if anyone knows how to hack that template let me know.

---

### Post by OzzyFrank on 2008-01-17
Oh, I just played around with trying to make other xml files based on that template, but after no results (they wouldn't appear) I just opened the original and changed hole="58.5pt" to 28.5. I suppose I should have clarified when asking about hacking the file that I had no idea how to convert mm to points (though at second glance mm and pt seem awfully similar?), so wanted the measurement of the blank centre of a full-print disc in points. That lucky guess looks OK, but I'll probably have to fine tune it. So I guess I should be asking does anyone know how I can get duplicate xml files with different names and settings within to be recognised, so I can have more CD tray templates load?

---

### Post by OzzyFrank on 2008-01-17
Me again. Thought I may as well paste the code from the xml file for people to look at. I gather you can alter some dimensions here for your own tray if using a different printer (a preview of the template shows a long narrow "page" with a circle near one end). The disc dimensions would stay the same. This is my edited one with the smaller hole:

[COLOR="Blue"]<?xml version="1.0"?>
<Glabels-templates xmlns="http://snaught.com/glabels/2.0/">
  <Template name="CanonPIXMA-directCD" size="Other" width="131mm" height="239mm" description="Canon PIXMA direct CD printing">
    <Label-cd id="0" radius="2.325in" hole="28.5pt" waste="0pt">
      <Layout nx="1" ny="1" x0="5mm" y0="70mm" dx="4.425in" dy="4.625in"/>
      <Markup-margin size="9pt"/>
    </Label-cd>
  </Template>
</Glabels-templates>[/COLOR]

So grab that, alter the width, height and layout, paste it into gedit or whatever and save it as an xml file in** /usr/share/glabels/templates**. (If you make one for your tray and it works great, try to make it available to others with the same model).

Now, if someone can tell me why the heck duplicates of this with different "Template name" and "description" aren't being recognised, but alterations to the original are noted after glabels is restarted, that would be great, hehe.

---

### Post by OzzyFrank on 2008-01-17
Thought I'd include a screenshot. You'll notice the size of the image is limited to the template, as the pic is actually much larger. To centre it correctly, just make the **X** and** Y** in ***Position*** **0.0**.

[IMG]http://www.ozzyfrank.com/Ubuntu/images/gLabels-Disc-Template.jpg[/IMG]

---

### Post by OzzyFrank on 2008-01-18
OK, figured out **how to get multiple CD templates to appear in the list**, for small and large centres. This xml template has references to Canon removed too, so anyone can use this after making sure of the tray size and layout:

[COLOR="DarkRed"]<?xml version="1.0"?>
<Glabels-templates>
  <Template name="CD-Tray-Small" size="Other" width="131mm" height="239mm" description="Disc in Tray (Small Centre)">
    <Label-cd id="0" radius="2.325in" hole="28.5pt" waste="0pt">
      <Layout nx="1" ny="1" x0="5mm" y0="70mm" dx="4.425in" dy="4.625in"/>
      <Markup-margin size="9pt"/>
    </Label-cd>
  </Template>
  <Template name="CD-Tray-Large" size="Other" width="131mm" height="239mm" description="Disc in Tray (Large Centre)">
    <Label-cd id="0" radius="2.325in" hole="58.5pt" waste="0pt">
      <Layout nx="1" ny="1" x0="5mm" y0="70mm" dx="4.425in" dy="4.625in"/>
      <Markup-margin size="9pt"/>
    </Label-cd>
  </Template>
</Glabels-templates>[/COLOR]

PS: I suppose you can name this file anything you want, but in trying to get other xml files to work, I noticed that only those with "-templates" before the extension would load... renaming my altered duplicate templates thus made gLabels unable to load... take that off the end of the original template and gLabels loads but the template doesn't. So name the file something like cd-tray-printing-templates.xml, and include other CD templates within the one file, like I have done above. Hope this helps someone!

---

### Post by OzzyFrank on 2008-01-18
[IMG]http://www.ozzyfrank.com/Ubuntu/images/gLabels-disc-templates.jpg[/IMG]

... Just so you can see the result. You can add more any time by editing the file (sudo gedit /usr/share/glabels/templates/cd-tray-printing-templates.xml - change the name of the xml file to suit). That's it from me, as now I can add more templates according to brands with more or less printng surface. That actually makes it better than CD Label Print in Windows, as with that you are limited in the size of hole and it won't stick in saved files or templates (I'm sure Droppix and the like are better). Now I just have to figure out how to convert mm to pt, as at closer look they aren't the same, and i doubt the pt is for percent. Cheers

---

### Post by Spanarn on 2008-02-03
Thanks for your gconf-editor help!

I have tested the settings you supplied and i have found that for my Canon PiXMA IP5000 the settings below works best.
If you run the Template Designer, i gLabels, it will explain the  of the layout codes in the xml file.

/Daniel

```
<?xml version="1.0"?>
<Glabels-templates>
  <Template name="CD-Tray-Small" size="Other" width="131mm" height="239mm" description="Canon PIXMA direct CD printing (Small Centre)">
    <Label-cd id="0" radius="2.325in" hole="28.5pt" waste="0pt">
      <Layout nx="1" ny="1" x0="6mm" y0="87mm" dx="4.425in" dy="4.625in"/>
      <Markup-margin size="2pt"/>
    </Label-cd>
  </Template>
<Template name="CD-Tray-Large" size="Other" width="131mm" height="239mm" description="Canon PIXMA direct CD printing (Large Centre)">
  <Label-cd id="0" radius="2.325in" hole="58.5pt" waste="0pt">
    <Layout nx="1" ny="1" x0="6mm" y0="87mm" dx="4.425in" dy="4.625in"/>
    <Markup-margin size="2pt"/>
    </Label-cd>
  </Template>
</Glabels-templates>
```

---

