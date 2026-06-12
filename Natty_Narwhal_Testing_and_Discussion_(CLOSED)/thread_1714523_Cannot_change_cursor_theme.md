---
title: "Cannot change cursor theme"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Atermoon on 2011-03-25
Is it something on my end or is changing the cursor really impossible in Natty right now? The option in ccsm seems to be gone aswell (at least I can't find it).

DMZ makes me cry :(


Edit: I just noticed that when my browser is loading a page the busy cursor switches to Oxygen and goes back to DMZ after the page is loaded. Rebooting doesn't help either just for the record.

---

### Post by douham on 2011-03-25
> **Atermoon said:**
> Is it something on my end or is changing the cursor really impossible in Natty right now? The option in ccsm seems to be gone aswell (at least I can't find it).

DMZ makes me cry :(


Edit: I just noticed that when my browser is loading a page the busy cursor switches to Oxygen and goes back to DMZ after the page is loaded. Rebooting doesn't help either just for the record.

I can change the mouse cursor the same as in maverick etc..Via all applications>appearance>themes>customize theme>pointer tab.

I don´t notice the cursor switching themes when web pages are loading

---

### Post by Atermoon on 2011-03-26
> **douham said:**
> I can change the mouse cursor the same as in maverick etc..Via all applications>appearance>themes>customize theme>pointer tab.

I don´t notice the cursor switching themes when web pages are loading

I guess it's something with my install then. For the time being I edited /usr/share/icons/default/index.theme and replaced DMZ-White with oxy-white (to get the Oxygen cursor).

---

### Post by kansasnoob on 2011-03-26
I've been too busy to explore why (I assume just due to some dev updates) but I also noticed my mouse pointer changed, and I tried changing it in the normal way, but no dice :)

---

### Post by MarcusA on 2011-03-26
Hey, I had the same problem, I wanted to use a downloaded cursor. It worked when I had my cursor on a link but other than that it switched to the original cursor. Now this fixed it for me.

[http://www.webupd8.org/2010/08/how-to-change-mouse-cursor-theme-in.html](http://www.webupd8.org/2010/08/how-to-change-mouse-cursor-theme-in.html)

You have to go find the name of the folder of the cursor you want to use in  /usr/share/icons/ , If the cursor you want to use is not there (like for me) you have to find it in /home/*username*/.icons (hidden folder) and copy the ursor theme you want to use to  /usr/share/icons/ (I did that using gksu nautilus since I don't really know how to copy paste stuff true the terminal lol). After you did that paste "gksu gedit /usr/share/icons/default/index.theme" in the terminal and edit the text like they show in the link I posted, hope it helps.

---

### Post by SENTINEL5000 on 2011-04-05
Ok, I've got a solution for this that works (at least for me) in Ubuntu 10.10. What I do is right click on desktop, select change desktop background, go to theme tab, then click on customize, go to cursor tab and click on the cursor you want, hit close and then check on a web page link you'll see the cursor changes back and forth from the new one and the old one.

Now right click your Compiz icon  in the top bar (for me)and go to select window decorator, change to GTK window decorator and you shall see your new cursor working, then change back to emerald decorator and done :D.

Again this is what works for me in 10.10, hope it helps.

---

### Post by lidex on 2011-04-05
Have tried all this and more to no avail. What's been going on for some time is white DMZ is default no matter what is selected in ccsm, gconf-editor, or display properties. I do see my selected cursor in terminal and mozilla apps?? Anyway, fixed it by updating alternatives:
```
sudo update-alternatives --config x-cursor-theme

```

---

### Post by lanetherif on 2011-04-12
It is so persistent that I tend to think of it as a feature. I had it in 9.10 (though I am not sure), 10.04, 10.10 and now in 11.04. I used to use the workaround mentioned [here ]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647"). For the time being I just gave up and am hoping that it will be really fixed when Natty is released.

---

