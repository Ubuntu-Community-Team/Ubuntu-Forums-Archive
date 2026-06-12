---
title: "change male voice to female in speech-dispatcher"
date: 2017-01-25
forum: Multimedia Software
---

### Post by MikeCyber on 2017-01-25
Hi
how to change male voice to female in speech-dispatcher?
Thanks

---

### Post by yancek on 2017-01-25
I've never used this software but you should be able to access all the info by opening a terminal and typing:  man speech-dispatcher to get all the details.  Or, you can go to the site below which is the manpage for it.  There should be a configuration file you can edit to make this selection as root using sudo with your text editor.  If you are using the standard Ubuntu with gedit, you would go to a terminal and enter:  

sudo gedit /etc/default/speech-dispatcher/speechd.conf

That (speechd.conf) is the file to edit and it does have the options you are looking for

 [http://manpages.ubuntu.com/manpages/zesty/man1/spd-say.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/spd-say.1.html)

---

