---
title: "How to adding entries to on screen menus?"
date: 2009-03-29
forum: Mythbuntu
---

### Post by tobiz on 2009-03-29
I want to add some entries to the on screen menu you can get when watching TV or playing back recordings.  The menu is brought up by the 'm' key and has entries for controlling screen filling, aspect ratio etc.  How is this config set up in Mythbuntu? I want to add entries to control my AV amp (Marantz SR5002) over its RS232 link.

---

### Post by tobiz on 2009-04-02
So far no replies. Can I assume it's not possible? Which is rather a shame since I can now control my SR5002 AV amp via its RS232 port and a UR86E X10 RF Remote for MythTV functions such as vol-up/down, mute etc. But there's a whole load of other functions on the SR5002 to control such as which Dolby system to use etc; a nice way of presenting the control to these when using Myth would be neat.

---

### Post by ian dobson on 2009-04-02
Hi,

All menus are saved in XML format so you can edit then using your text editor.

The files are stored in /usr/share/mythtv I think. 
Note if you do edit the menu files make sure you make a backup, when you do an upgrade that will be overwritten.

For example the shutdown button looks like this:-
```
   <!-- <button>
     <type>SHUTDOWN</type>
     <text>Shutdown</text>
     <text lang="SV">AvstÃ¤ngning</text>
     <text lang="DK">Sluk</text>
     <text lang="NL">Uitschakelen</text>
     <text lang="DE">Beenden</text>
     <text lang="ET">Seiska</text>
     <text lang="PT">GravaÃ§Ãµes/text>
     <text lang="NL">Afsluitenr</text>
     <text lang="RU">ÐÐ°Ð²ÐµÑÑÐµÐ½Ð¸Ðµ ÑÐ°Ð±Ð¾ÑÑ</text>
     <text lang="PL">Zamknij system</text>
     <text lang="HE">××××os</text>
     <action>SHUTDOWN</action>
   </button> -->
```

and is saved in the  mainmenu.xml file.

Regards
Ian Dobson

---

