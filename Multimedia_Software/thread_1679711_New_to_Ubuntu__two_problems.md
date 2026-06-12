---
title: "New to Ubuntu : two problems"
date: 2011-02-01
forum: Multimedia Software
---

### Post by gmolivier on 2011-02-01
First problem is i cannot get VLC or any other video app to work.  VLC opens, but video does not play.  I have deleted and re-installed it twice...no change.  None of the other video apps work: Kaffeine, MPlayer, Movie Player Totem.  What can i do to make any of them work so i can play DVD movies?

Second Problem.   I get various newsletter in my email client, Evolution.  Newsletters have links to the stories.  Clicking on a link opens the link in my browser, Firefox.  What it doesn't do is go to that page in the browser.  I must click on the browser tap to reach the story.  How can i configure the email client to open the browser?

Thanks,

gmo

---

### Post by irv on 2011-02-01
> **gmolivier said:**
> First problem is i cannot get VLC or any other video app to work.  VLC opens, but video does not play.  I have deleted and re-installed it twice...no change.  None of the other video apps work: Kaffeine, MPlayer, Movie Player Totem.  What can i do to make any of them work so i can play DVD movies?

Second Problem.   I get various newsletter in my email client, Evolution.  Newsletters have links to the stories.  Clicking on a link opens the link in my browser, Firefox.  What it doesn't do is go to that page in the browser.  I must click on the browser tap to reach the story.  How can i configure the email client to open the browser?

Thanks,

gmo
For problem one: Make sure you installed the “Ubuntu restricted extras”. To do this just go to the Ubuntu Software Center under Applications menu, and do a search for codec. See screen shot.
[ATTACH]182472[/ATTACH]

For Problem two: I am not sure what is wrong. Mine just works. I click on a link and it open in Firefox.

---

### Post by gmolivier on 2011-02-01
...thanks, Irv, did as you suggested but VLC still not plays...re-booted, of course

gmo

---

### Post by irv on 2011-02-01
> **gmolivier said:**
> ...thanks, Irv, did as you suggested but VLC still not plays...re-booted, of course

gmo

I am not sure if this will work but it is worth a try.
Now that you have the codec's installed, try completely removing VLC and then re-install it again. As I remember I had this problem awhile ago and I think this fixed it.
Give it a shot and see what happens.

---

### Post by gmolivier on 2011-02-01
...that didn't work, but VLS recognized the DVD by name of movie...a step forward, i think.

---

### Post by irv on 2011-02-01
> **gmolivier said:**
> ...that didn't work, but VLS recognized the DVD by name of movie...a step forward, i think.

Maybe someone else can jump in at the is point if they have something else you can try. If you try to run VLC from a command line in a terminal do you get any error messages?
When I do this I do not get any error. see my screen shot.
[ATTACH]182505[/ATTACH]

---

### Post by gmolivier on 2011-02-02
I don't know how to get to a terminal, or even what that means.  I would like to know if Ubuntu has something like "Explore" in Windows, where i can go and look at the various files inside the o.s.

It is very annoying that i cannot go straight to a browser from an email link...there is probably a simple checkbox left unchecked somewhere...same with VLC.

Thanks for your imput

---

### Post by cchhrriiss121212 on 2011-02-02
Ubuntu needs an extra package to play DVDs (for legal reasons it is not installed by default). Open Accessories>Terminal and paste this:[FONT=monospace]
[/FONT]```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by irv on 2011-02-02
To look at your files in your home directory go to Places>Home Folder. This is where all your files will be located. It is just like the file manager in windows. It is called Nautilus. Here is a screen shot.
[ATTACH]182541[/ATTACH]

---

### Post by mastablasta on 2011-02-02
> **cchhrriiss121212 said:**
> Ubuntu needs an extra package to play DVDs (for legal reasons it is not installed by default). Open Accessories>Terminal and paste this:
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```
 
 
just to add to this you will be asked for oyur user password. when you type nothing will show but it does register it. so just type it in and press enter.
 
for your second issue, when you click on the link where does it open the connection?
Check in the options there is probably a setting somewhere whre browser is chosen. if firefox is your default browser it should also help. sorry i can't help more but i am away from Ubuntu computer...
 
or try this: [http://osdir.com/ml/evolution-list/2009-08/msg00139.html](http://osdir.com/ml/evolution-list/2009-08/msg00139.html)

---

### Post by gmolivier on 2011-02-02
Still not playing, Chris...VLC seems to want to play dvd, but something stops it...thanks for your help.  After adding the code you suggest, Terminal does not ask me to save it, and when i go searching for the text, i cannot find it...maybe Terminal did not save the code?

gmo

---

### Post by gmolivier on 2011-02-02
...ok, that did it...i didn't understand fully earlier how to do it in Terminal...so, now i can watch movies...thanks loads!

...re: problem two...when i click on a link in a email newsletter, if my browser (Firefox) is not already open, clicking the linik will open it to the page selected.   If the browser is already open, clicking a link will open the page in the browser, but not go TO the browser...i must click on the browser button to go there...don't  know if i'm being clear or not.

---

### Post by killfall on 2011-02-02
Yeah I understand. I've noticed that a lot but haven't found a solution. If you have a program like gedit open and you open a text file from nautilus it wont bring the gedit window to the front. I think that it's just something you're going to have to live with but I could be wrong.:roll:

---

### Post by irv on 2011-02-02
> **gmolivier said:**
> ...ok, that did it...i didn't understand fully earlier how to do it in Terminal...so, now i can watch movies...thanks loads!

...re: problem two...when i click on a link in a email newsletter, if my browser (Firefox) is not already open, clicking the linik will open it to the page selected.   If the browser is already open, clicking a link will open the page in the browser, but not go TO the browser...i must click on the browser button to go there...don't  know if i'm being clear or not.
Mine dose the same thing. I think this is normal. It is just the way the code is written for this program. If you want to change it you need to get the code and do it yourself. If you are not a programmer then just leave it to them to maybe make the change someday. You could also report it as a bug to be fixed.

---

### Post by gmolivier on 2011-02-02
...thanks everybody

gmo

---

### Post by Swagman on 2011-02-02
How have you got your preferred Applications configured ?

System/Prefs > Preferred Apps

[img]http://localhostr.com/file/eCIk6ti/Ubuntu151.jpeg[/img]

---

### Post by gmolivier on 2011-02-02
...hey, thanks, Swagman...that did it!

---

### Post by killfall on 2011-02-03
Swagman.

I'm having a couple of problems with gedit and Komodo. If I have Komodo open and I open another PHP file then Komodo doesn't come to the front. Is there any way of changing that?

---

### Post by irv on 2011-02-04
> **killfall said:**
> Swagman.

I'm having a couple of problems with gedit and Komodo. If I have Komodo open and I open another PHP file then Komodo doesn't come to the front. Is there any way of changing that?

You seem to be asking for help with another problem in this thread, why don't you start a new thread with this problem.
Just for the record, I seem to remember the app indicator in the panel flashes which means something new has open. I know it does it in firefox. It doesn't put the focus on it, but it tells you something is going on.

---

