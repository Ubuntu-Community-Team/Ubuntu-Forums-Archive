---
title: "Mplayer cyrillic subtitles problem"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by Fechter on 2008-02-20
Whenever I try to load the cyrillic subtitles, I don't get letters displayed unproperly. Firstly I got them line... I think it was Vietnamese or some other, but at least not ?????????
Then I went into the properties menu in Mplayer and set encoding first to Win1251 after that to UTF8, but in both cases the result was
[_ _ _ _ _ _ _ _ ] , [_ _ _ ] and so on. Does anyone know how to fix this?

---

### Post by Fechter on 2008-02-21
I have found a program called "recode" which could change the encoding of subtitles. If I change the encoding setting in Mplayer and use recode to change the encoding of the .sub files maybe I could fix my problem.. if no-one has any idea, can someone tell me how to use recode or if there is a better program to do the trick?:confused:

---

### Post by Fechter on 2008-02-21
Heloo

---

### Post by shock17 on 2008-03-17
i have exactly the same problem with gnome-mplayer under fedora8 
even if i use "recode" to change the file encoding to windows-1251 or UTF-8 - it still doesnt work - i get only "~:!"?????? ? :"";? ? `1? ?  


&#1072;&#1088;&#1077; &#1073;&#1077; &#1082;&#1086;&#1087;&#1077;&#1083;&#1077;&#1090;&#1072; &#1082;&#1072;&#1082; &#1076;&#1072; &#1089;&#1080; &#1086;&#1087;&#1088;&#1072;&#1074;&#1103; &#1089;&#1091;&#1073;&#1090;&#1080;&#1090;&#1088;&#1080;&#1090;&#1077; :)

---

### Post by mou5e on 2008-07-05
&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1096; &#1084;&#1087;&#1083;&#1077;&#1081;&#1098;&#1088;, &#1076;&#1077;&#1089;&#1077;&#1085; &#1073;&#1091;&#1090;&#1086;&#1085; &#1085;&#1072; &#1084;&#1080;&#1096;&#1082;&#1072;&#1090;&#1072;, &#1055;&#1088;&#1077;&#1092;&#1077;&#1088;&#1077;&#1085;&#1089;&#1080;&#1089;, &#1090;&#1072;&#1073; &#1057;&#1098;&#1073;&#1090;&#1072;&#1081;&#1090;&#1098;&#1083;&#1089; &#1077;&#1085;&#1076; &#1054;&#1091;&#1045;&#1089;&#1044;&#1080;, &#1045;&#1085;&#1082;&#1086;&#1076;&#1080;&#1085;&#1075; - Cyrillic Windows (CP1251). &#1055;&#1086;&#1089;&#1083;&#1077; &#1086;&#1090;&#1080;&#1074;&#1072;&#1096; &#1085;&#1072; &#1090;&#1072;&#1073; &#1060;&#1086;&#1085;&#1090; &#1080; &#1090;&#1072;&#1084; &#1085;&#1072; &#1077;&#1085;&#1082;&#1086;&#1076;&#1080;&#1085;&#1075; &#1076;&#1072;&#1074;&#1072;&#1096; Unicode. 

&#1058;&#1074;&#1072; &#1086;&#1087;&#1088;&#1072;&#1074;&#1080; &#1084;&#1086;&#1081;&#1090;&#1077; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1080;.

Open mplayer, right-mouse-button -> Preferences, tab Subtitles & OSD, Encoding: Cyrillic Windows (CP1251). After that go to tab Font and there set the encoding to: Unicode.

That fixed my problems.

---

### Post by jonian_g on 2008-07-06
Get the new gnome-mplayer 0.6.3. This may solve your problem.

[http://code.google.com/p/gnome-mplayer/](http://code.google.com/p/gnome-mplayer/)

You have to compile it. No .deb yet ready.

---

