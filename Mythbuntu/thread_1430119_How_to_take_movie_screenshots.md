---
title: "How to take movie screenshots?"
date: 2010-03-15
forum: Mythbuntu
---

### Post by killabee44 on 2010-03-15
Guys,

I would like to take some movie screenshots and use them as fanart. Is there a key combination in Myth? Thanks.

---

### Post by nickrout on 2010-03-15
Bind a key to SCREENSHOT  in the TV Playback context using MythControls. Then, hit that key during playback or when paused. Then, check $HOME/.mythtv for the screenshot image.

[http://www.gossamer-threads.com/lists/mythtv/theming/392813](http://www.gossamer-threads.com/lists/mythtv/theming/392813)

---

### Post by 4dognight on 2010-03-16
I had also read that post, but it wasnt exactly clear on what to do. I looked in the keybindings table in the DB and saw the SCREENSHOT entry. So, does this mean the screenshot facility is there but not implemented via a key? Kind of like an undocumented feature?  Has anybody actually tried this with success? Steps involved? I was hoping to make some fanart for shows that are missing it.

---

### Post by nickrout on 2010-03-16
Read the whole thread, the instructions are there!

---

### Post by 4dognight on 2010-03-16
ok, got it to work. But I still say I cant find anything in that posting on how to setup that keybinding. It refers to 'mythcontrols'. When I google mythcontrols, it leads me to mythtv document that says.

Note: Mythcontrols functionality will be merged into mythfrontend and no longer available as a plugin with the upcoming release of 0.22 

Now, I did see keybindings in mythweb. I updated it to a ctrl-s and clicked on save. But it did nothing. So I updated the entry in the database directly to use a ctrl-s. That worked, it  even pops a window up on the screen stating it made a screenshot. 

The file is stored in ~/.mythtv . So, what is the screenshot directory location in the FE config for? It is pointing to /tmp.

I still hav yet to find anything that mentions screenshot capability in any myth documentation. I wonder what other features are out there undocumented? :-)

---

### Post by killabee44 on 2010-03-16
Thanks for the info guys.....

4dognight, when you say: "I updated teh entry in the database directly" What exactly do you mean?

---

### Post by nickrout on 2010-03-16
Keybindings is also available in the frontend somewhere in the menus.

---

### Post by kja999 on 2010-03-17
Keybindings are also shown in mythweb in a very easy to use manner ...

---

### Post by 4dognight on 2010-03-17
> **killabee44 said:**
> Thanks for the info guys.....

4dognight, when you say: "I updated teh entry in the database directly" What exactly do you mean?

I installed the MySQL query browser and ran the following command in the mythconverg DB,

update keybindings set keylist = 'Ctrl+S' where action = 'SCREENSHOT'

You could also run it using the command line tool for mysql

echo "update keybindings set keylist = 'Ctrl+S' where action = 'SCREENSHOT'"|mysql -u mythtv -p  -h 192.168.2.6 -D mythconverg

*substitute your IP and enter your password when prompted

---

