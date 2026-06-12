---
title: "No way to close firefox pop ups?"
date: 2011-02-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2011-02-26
I have a  few pop ups for which i cant locate the close button. Seems like i will need a user manual for unity.I cant figure it out well.

---

### Post by cariboo on 2011-02-26
Show us a screenshot.

---

### Post by rajeev1204 on 2011-02-26
> **cariboo907 said:**
> Show us a screenshot.

Look,




I searched on global menu at top but dont see nothing, then i toggled maximise button in firefox but the pop ups dont have window buttons or borders.

---

### Post by cariboo on 2011-02-26
It looks like compiz crashed, try:

```
compiz --replace
```

in a terminal to restart compiz.

**edit** I had a second look after typing the above, when you click on each window, doesn't the global menu become active, so that you can close the window? Just move your mouse over where it says Firefox 4.0 Beta in the top panel to reveal the menu

See the screenshot

---

### Post by gooeykablooey on 2011-02-26
You can close them by making them active and then using alt+F4

I had this problem earlier today, I ran sudo apt-get update and it installed a whole bunch of packages, but then there were no window decorations. Then, I opened up synaptic and attempted to update everything again. There were some other updates to unity and compiz that required some new packages to be installed. Once these updates were applied, I logged out and back in again, and now all is good.

---

