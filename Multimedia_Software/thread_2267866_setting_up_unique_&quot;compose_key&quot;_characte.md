---
title: "setting up unique &quot;compose key&quot; characters"
date: 2015-03-04
forum: Multimedia Software
---

### Post by sgriggly on 2015-03-04
hey guys i have a funny problem. 

i am trying to set up my own "compose key" characters. what i've done so far is: 

located the "Compose" file in /usr/share/X11/locale/en_US.UTF-8/Compose

opened it up using "gksu nautilus" folder

i edited the lines by adding two new "multi_key" strings, here they are:

<Multi_key> <s> <h>              	: "&#643;"   U0283 # IPA SH-LIGATURE
<Multi_key> <z> <h>              	: "&#658;"   U0292 # IPA ZH-LIGATURE

and edited one existing multi_key string: 

<Multi_key> <c> <h> 	         	: "ç"   ccedilla # LATIN SMALL LETTER C WITH CEDILLA

and DELETED the Multi-key string that used to be called by 'c' + 'h'

then i saved the file. (it is well and truly saved, i've done a restart and re-opened everything, the lines i changed are still there). 

now, here's the weird thing. not only are the new lines i added in not working, but when i type "compose key" then "c" then "h"... i get the OLD symbol recall, "&#543;"

guys, this line isn't even in my "Compose" file any longer. my keyboard must be referring to some OTHER file for its "Compose Key" code... any ideas where it is or what's happening?

---

### Post by sgriggly on 2015-03-05
anyone?... 

modifying /usr/share/X11/locale/en_US.UTF-8/Compose doesn't change my "compose key" shortcuts...

---

### Post by shantiq on 2015-03-05
sgriggly have you tried pressing **Shift**[COLOR=#333333][FONT=Ubuntu]+[/FONT][/COLOR]**[AltGr]("https://help.ubuntu.com/community/AltGr")   **on British Keyboard layout and then one after the other ","  then c

you get your c cedilla that way no need to do more   ç


also great [howto]("https://help.ubuntu.com/community/ComposeKey#Third_and_fourth_level_choosers")  here

---

### Post by sgriggly on 2015-03-05
yes. i can get the ç character with the short code "compose key" then "comma" then "c"

my question is, why is that *still* the short code after i've already modified the "compose key" file? 

in other words, my compose key is working great. in the link you sent, my question comes at the bottom, here: 

"To create your own set of compose keys copy the file /usr/share/X11/locale/en_US.UTF-8/Compose (or if you prefer the equivalent file for your locale) to your home directory as .XCompose  # cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose  and edit this file." 

not sure what is meant here by "copying to home directory as .XCompose". can you clarify? i tried it, doesn't work. 

before, i simply edited the file and saved in the same location.

---

### Post by Impavidus on 2015-03-05
It means "copy the file to your home directory and rename it **.XCompose**."

That help page also says> The Gnome hard coding can be overruled in favour of  the original Xwindow Input Method (XIM) by setting the environment  variable GTK_IM_MODULE. This can be set in the /etc/environment file, but if the machine has more than one user then it is best set from the home directory on a per user basis by modifying ~/.gnomerc or  ~/.Xsession```
export GTK_IM_MODULE="xim"
```Try setting that environment variable.

---

### Post by sgriggly on 2015-03-05
ok that's what i THOUGHT it meant, and i already did that... i think. i'm sorry, i've had Ubuntu for years now, but i'm a continual "noob". 

can you spell it out for me? what is the exact location "home directory" refers to? i've already copied the file and renamed it and it's now in my folder named "home". (it didn't work). i also have a copy named the same .XCompose in "File System" - "home". (it also isn't doing anything that i can tell). 

the information you provided is nice, but i don't understand what it means. can you translate for me? i see... "blah blah blah... code:" i typed the code into the terminal and pressed enter... nothing happened. 

apologies, but i need some specific instructions.

---

