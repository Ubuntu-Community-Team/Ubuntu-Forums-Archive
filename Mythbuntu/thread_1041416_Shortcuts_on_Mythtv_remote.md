---
title: "Shortcuts on Mythtv remote"
date: 2009-01-16
forum: Mythbuntu
---

### Post by dad311 on 2009-01-16
I have 4 shortcuts on my Mythtv remote labled "Radio", "Music", "Pictures" and "Videos".

irw sees the buttons being pressed, but there is no action assigned to them.


How can I assign the "Music" button to jump to the music menu in Mythtv.


thx

---

### Post by scary_jeff on 2009-01-22
All the interactions between lirc and mythtv should be defined in ~/.lircrc . If it already exists, the file is pretty self explanatory, and there's a list of all the default mythtv command keys _[here]("http://www.mythtv.org/docs/mythtv-HOWTO-11.html")_. If not, just google lircrc.

I am just in the process of working out why ALT+H, ALT+V etc (that's what the 'home' and 'video' buttons are assigned to in my lircrc) don't seem to do anything. They don't do anything even using the keyboard, so it's probably a case of just finding out where to configure this in mythtv. I'll come back if I find the answer.

---

### Post by dad311 on 2009-01-24
After a lot of searching Ive got the jump buttons figured out.  Here is what I did to setup my jump key(s).  Below is an example for the Music button in about 3 steps.

1) Setup Key Bindings in Mythtv.  I used the mythweb todo this(http://<mythtv ip>/mythweb) you call also do this via the menus.  In either place set "Play Music" to Key Binding [COLOR="Red"][COLOR="Red"]F5[/COLOR][/COLOR].

2) On Mythtv box open a terminal window and type irw.  Press the button on the remote you would like to assign to jump to music.  The irw window will display the [COLOR="Red"]button name[/COLOR] and the [COLOR="Red"]remote name[/COLOR].



3) Edit /home/<user>/.lirc/mythtv. At the bottom of the file append the new info for the music jump button.  Restart Mythtv( I use Ctrl-alt-backspace).

 begin
remote = [COLOR="Red"]mceusb[/COLOR]
	button = [COLOR="Red"]Music[/COLOR]
	prog   = mythtv
	repeat = 0
	config = [COLOR="Red"]F5[/COLOR]
end

---

### Post by rhpot1991 on 2009-01-24
> **dad311 said:**
> After a lot of searching Ive got the jump buttons figured out.  Here is what I did to setup my jump key(s).  Below is an example for the Music button in about 3 steps.

1) Setup Key Bindings in Mythtv.  I used the mythweb todo this(http://<mythtv ip>/mythweb) you call also do this via the menus.  In either place set "Play Music" to Key Binding [COLOR="Red"][COLOR="Red"]F5[/COLOR][/COLOR].

2) On Mythtv box open a terminal window and type irw.  Press the button on the remote you would like to assign to jump to music.  The irw window will display the [COLOR="Red"]button name[/COLOR] and the [COLOR="Red"]remote name[/COLOR].



3) Edit /home/<user>/.lirc/mythtv. At the bottom of the file append the new info for the music jump button.  Restart Mythtv( I use Ctrl-alt-backspace).

 begin
remote = [COLOR="Red"]mceusb[/COLOR]
	button = [COLOR="Red"]Music[/COLOR]
	prog   = mythtv
	repeat = 0
	config = [COLOR="Red"]F5[/COLOR]
end

A few pointers.  Make sure this button is not used by anything else, jump points take priority over any other event.  If you are doing this remotely you can restart the frontend by doing the following: sudo /etc/init.d/gdm restart

---

### Post by scary_jeff on 2009-02-06
> **scary_jeff said:**
> All the interactions between lirc and mythtv should be defined in ~/.lircrc . If it already exists, the file is pretty self explanatory, and there's a list of all the default mythtv command keys _[here]("http://www.mythtv.org/docs/mythtv-HOWTO-11.html")_. If not, just google lircrc.

I am just in the process of working out why ALT+H, ALT+V etc (that's what the 'home' and 'video' buttons are assigned to in my lircrc) don't seem to do anything. They don't do anything even using the keyboard, so it's probably a case of just finding out where to configure this in mythtv. I'll come back if I find the answer.

The solution for me was that I didn't have the mythcontrols plugin installed. Once I had this, it was trivial to set up these 'jump points'. Mythcontrols is available through apt-get.

---

