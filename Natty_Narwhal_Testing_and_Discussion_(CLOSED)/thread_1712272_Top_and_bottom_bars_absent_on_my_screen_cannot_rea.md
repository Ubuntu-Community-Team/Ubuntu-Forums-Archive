---
title: "Top and bottom bars absent on my screen cannot really see a way to bring them back"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shantiq on 2011-03-22
hi there as you can see on attached image got no top or bottom bar and therefore cannot do much


got my terminal is there any way to make them appear


got nvidia going and compiz


all clever suggestions welcome    thanx   shan

---

### Post by sgage on 2011-03-22
What happens when you issue the command 

```
gnome-panel
```

in your terminal?

---

### Post by shantiq on 2011-03-22
hi there thanx for reply


found [this ]("http://ubuntuforums.org/showpost.php?p=10506654&postcount=6")which works


```
gnome-panel --replace
```


but i need to have the terminal on after that


weird:KS

---

### Post by sgage on 2011-03-22
Issue that command from Alt-F2, and you won't have that problem...

---

### Post by shantiq on 2011-03-22
thank you sgage will do

---

### Post by shantiq on 2011-04-04
the problem was that gnome-panel was not loading at the start




so going to system/preferences/startup applications and add gnome-panel to the list corrects that

---

### Post by r-senior on 2011-04-04
@shantiq: nice graphics (desktop & your forum avatar) - are they your own artwork?

---

### Post by Zorgoth on 2011-04-04
Also if you ever need to run something from the terminal and then close the terminal, you can use:

your_command &
disown

& will make it run in the background so you can continue to type commands in the terminal (the terminal may have output in it but if you type a command it will run), and after you run disown you can safely close the terminal.

---

### Post by shantiq on 2011-04-04
> **r-senior said:**
> @shantiq: nice graphics (desktop & your forum avatar) - are they your own artwork?

thank you Senior  yes they are [mine]("http://www.saatchionline.com/shantiq") I am an artist/musician

Part of the reason why i like Ubuntu so much it looks ten times better than any other OS visually

---

### Post by lidex on 2011-04-04
> **shantiq said:**
> the problem was that gnome-panel was not loading at the start




so going to system/preferences/startup applications and add gnome-panel to the list corrects that

That shouldn't be necessary. On the login screen what session have you chosen? You probably want to check the files in /usr/share/gnome-session/sessions. Do they look like these?
```
**2d-gnome.session**
[GNOME Session]
Name=Failsafe GNOME
Required=windowmanager;panel;filemanager;
Required-windowmanager=metacity
Required-panel=gnome-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;

**classic-gnome.session**
[GNOME Session]
Name=Classic GNOME
Required=windowmanager;panel;filemanager;
Required-windowmanager=gnome-wm
Required-panel=gnome-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
IsRunnableHelper=/usr/lib/nux/unity_support_test --compiz
FallbackSessionsID=GNOME2d
GNOME2d=2d-gnome

**gnome.session**
[GNOME Session]
Name=GNOME
Name[as]=GNOME
Name[ast]=GNOME
Name[br]=GNOME
Name[ca@valencia]=GNOME
Name[crh]=GNOME
Name[en@shaw]=·&#66652;&#66671;&#66676;&#66661;
Name[fy]=GNOME
Name[mai]=&#2327;&#2344;&#2379;&#2350;
Name[nds]=GNOME
Name[ps]=&#1707;&#1606;&#1608;&#1605;
Name[ug]=GNOME
Name[uz]=GNOME
Name[uz@cyrillic]=GNOME
Required=windowmanager;panel;filemanager;
Required-windowmanager=gnome-shell
Required-panel=gnome-shell
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
IsRunnableHelper=/usr/lib/gnome-session-is-accelerated
FallbackSessionsID=FallbackClassicGnome
FallbackClassicGnome=classic-gnome

**ubuntu.session**
[GNOME Session]
Name=Ubuntu
Required=windowmanager;panel;filemanager;
Required-windowmanager=compiz
Required-panel=compiz
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
IsRunnableHelper=/usr/lib/nux/unity_support_test
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.
```

---

