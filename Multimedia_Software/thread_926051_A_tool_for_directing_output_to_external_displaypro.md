---
title: "A tool for directing output to external display/projector/TV"
date: 2008-09-21
forum: Multimedia Software
---

### Post by AlesUbu123 on 2008-09-21
Hello all!

If you are finding it hard to navigate through all the possible commands in the terminal and if you would like to get your external display/projector/TV working easily, then you can check out this page:[[COLOR="Blue"]http://tadeboro.googlepages.com/xdisco]("http://tadeboro.googlepages.com/xdisco")[/COLOR]

My friend, Tadej, has created this little perl script, called **[COLOR="Red"]x[/COLOR][COLOR="YellowGreen"]D[/COLOR][COLOR="MediumTurquoise"]i[/COLOR][COLOR="DarkOrchid"]s[/COLOR][COLOR="YellowGreen"][COLOR="Cyan"]C[/COLOR][/COLOR][COLOR="DarkOrange"]o[/COLOR]** (**X** **Dis**play **Co**nfigurator) to spare me some work (and reading). It is a front-end to command-line tool xrandr. You need *xrandr* and *libgtk2-perl* packages installed to get it working and then you can start it by writing this command in the terminal: ```
perl xDisCo.pl
```

When you plug-in a new external display or projector press "Rescan" button and choose the preffered resolution under the coulumn VGA, LVDS or TV. 

Unlike native Ubuntu and Kubuntu configuration tools, this has worked perfectly for me and I wanted to share it with you. I have tested it on Ubuntu/Kubuntu 8.04. And just a note: The author states that it is an alpha release software, so please don't blame me if anything goes wrong. 

Have a nice day!

---

