---
title: "dual monitor bug?"
date: 2011-03-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ngsupb on 2011-03-17
I have a problem with a second monitor. I configure it as usually through nvdia-settings( set it to my main ), it saves a new xorg.conf. It works fine. But when I boot without the external monitor, unity is messed completely. Deleting the xorg.conf file fixes the issue. 

Is there a way to trace and fix it?

---

### Post by petersonja on 2011-03-30
I use an updated Natty, I configure dual-monitor (Seperate X) in nvidia-settings. But there isn't panel and launcher on the second monitor and the window decoration is still missing. It is a known bug? And if yes, any progress in this case?

---

### Post by geek.de.nz on 2011-03-30
[http://ubuntuforums.org/showthread.php?p=10617239#post10617239](http://ubuntuforums.org/showthread.php?p=10617239#post10617239)

Not sure if this is relevant, but try the above link.

---

### Post by petersonja on 2011-03-30
> **geek.de.nz said:**
> [http://ubuntuforums.org/showthread.php?p=10617239#post10617239](http://ubuntuforums.org/showthread.php?p=10617239#post10617239)

Not sure if this is relevant, but try the above link.

I haven't got problem with resoultion. My problem is the second screen hasn't got a panel.

---

### Post by Amaranth on 2011-03-30
Compiz no longer supports multiscreen (Separate X) so you have to manually start it from a terminal on the second screen.

---

### Post by petersonja on 2011-03-30
> **Amaranth said:**
> Compiz no longer supports multiscreen (Separate X) so you have to manually start it from a terminal on the second screen.

Oh, this isn't a good news. And is it a permanent decision or is it a bug? Can you tell me what command I need to run in terminal?

---

### Post by ronparent on 2011-03-30
> Originally Posted by Amaranth  
Compiz no longer supports multiscreen (Separate X) so you have to manually start it from a terminal on the second screen.

It's just as well I never learned that. I've got two monitors working as usual with the desktop spanned over the two. I do have the option of the same image on both.

---

### Post by petersonja on 2011-03-30
> **ronparent said:**
> It's just as well I never learned that. I've got two monitors working as usual with the desktop spanned over the two. I do have the option of the same image on both.

It's okay, but I would like two seperated X, coz my other screen is a TV. And If I want to see a movie, I am only want to see on that screen.

---

### Post by Amaranth on 2011-03-30
It's not a bug, it was an intentional design decision. There is no reason for compiz to manage multiple screens because it can't do anything special across the screens. On the second screen you should just need to run `compiz` from a terminal but you may need to run `unity-window-decorator` as well.

---

### Post by petersonja on 2011-03-31
> **Amaranth said:**
> It's not a bug, it was an intentional design decision. There is no reason for compiz to manage multiple screens because it can't do anything special across the screens. On the second screen you should just need to run `compiz` from a terminal but you may need to run `unity-window-decorator` as well.

Oh, I understand it. But what is the solution of the problem when you want two seperate X? Is Ubuntu (Unity) need to manage it? Or how is it works on Natty? (Sorry for my noob questions, but this isn't clear for me.)

---

### Post by garypat on 2011-04-03
> **petersonja said:**
> Oh, I understand it. But what is the solution of the problem when you want two seperate X? Is Ubuntu (Unity) need to manage it? Or how is it works on Natty? (Sorry for my noob questions, but this isn't clear for me.)

i put the screens in twin mode and it works like xenerama just drag windows to second moniter

---

