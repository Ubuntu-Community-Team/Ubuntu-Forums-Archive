---
title: "Myth Frontend GUI Font Size"
date: 2011-10-20
forum: Mythbuntu
---

### Post by brian_hayward on 2011-10-20
I am running mythbuntu 10.10/mythtv 0.23.1.  I have not upgraded my television to any kind of high def television yet and so i am obviously stuck using a tube tv.  I want to use my mythtv as more of a Media Center rather than just a box that i record shows on to watch later, but trying to read the mythtv menus on my square tv is difficult at best.  I have been googling around and i found a wiki page for mythtv ([http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend]("http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend")) which stated i should go to my mythfrontend menu -> setup -> appearance -> QT and i should have options to change font size.  When i get to the QT portion of the menu i see no options to adjust font size. the wiki stated at the top it was up to date "to MythTV version 0.23".  Any suggestions, ideas, or any kind of help with this issue is greatly appreciated.  Thanks.

Brian

---

### Post by JamesNorris on 2011-10-20
I think font sizes were hard-coded to the themes and not editable from within myth as of 0.23

You'll need to open up a couple of your theme's xml files and change the font sizes. 

eg. open up base.xml for the Mythbuntu theme and the font sizes are defined at the top

```
 <!-- Base Font Definitions -->
    <fontdef name="basesmall" face="DejaVu Sans">
        <size>FONT SIZE HERE</size>
        <color>#FFFFFF</color>
    </fontdef>
```

it continues for a few iterations to define the size of other used fonts after that,  I think there are five of them you'll need to change all together.

---

