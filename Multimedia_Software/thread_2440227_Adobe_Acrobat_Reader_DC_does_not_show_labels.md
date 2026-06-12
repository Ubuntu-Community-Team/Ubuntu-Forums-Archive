---
title: "Adobe Acrobat Reader DC does not show labels"
date: 2020-04-07
forum: Multimedia Software
---

### Post by rubencioak on 2020-04-07
Hi,

I am new to Ubuntu and I am trying to intall Adobe Acrobat Reader DC, however when I install it from the "software store" the labels fail to show up. some pictures may clarify:

[ATTACH=CONFIG]285452[/ATTACH]

[ATTACH=CONFIG]285453[/ATTACH]

Any help would be appreciated

KR
Ruben

---

### Post by slickymaster on 2020-04-07
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by Holger_Gehrke on 2020-04-07
If you had taken the time to read the description and the ratings, you'd know that this package is a snap containing the windows compatibility layer Wine and the Windows version of the program and is rated as 'very close to completely unusable'. 

A look in the app-db on winehq.org gives me this [page]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32266"), that says you need some Microsoft fonts named Segoe UI to display text on labels and in dialogs. Installing those might not help because of snap-confinement and would be illegal even if you had a valid Windows license because of the terms of Microsoft's License for the font. There is supposedly a lookalike open source font, but that wouldn't help you much, since Acrobat reader asks the system for 'Segoe UI' and not for whatever the other one is called. You might be able to set up an alias for the font so another font is used when a program asks for 'Segoe UI'. Details on how to do that can be found in the file /usr/share/doc/fontconfig/fontconfig-user.html, which should be installed on your system.

Holger

---

### Post by rubencioak on 2020-04-08
I will take this into account for next posts, Thanks!!

---

