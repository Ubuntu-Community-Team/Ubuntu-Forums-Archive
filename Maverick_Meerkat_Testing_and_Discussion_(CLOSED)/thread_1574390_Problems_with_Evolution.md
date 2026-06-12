---
title: "Problems with Evolution"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Maupertus on 2010-09-14
Hi everyone,

Since testing Meerkat after the Beta, I've been experiencing a lot of problems with Evolution. I had a couple of problems with the 2.28 iteration of Evo in Lucid, but after the adding of a 2.30 PPA, most of these issues were resolved. In Meerkat the Evo window keeps 'jumping' or shifting when clicking certain buttons or when changing between functions (mail, calendar, tasks etc) 

I've had problems with this issue on both my netbook and desktop, but I've never found the origin and it has been resolved often without active participation of my part.

Anyone have any idea what is causing this in Maverick?

On a different note, is it possible to install Evolution Express in a normal Gnome setting? I have tested Unity, didn't like it, but I did like Evolution Express!

Thanks!

---

### Post by qamelian on 2010-09-14
> **Maupertus said:**
> On a different note, is it possible to install Evolution Express in a normal Gnome setting? I have tested Unity, didn't like it, but I did like Evolution Express!

There is nothing to install. The Express interface is built right into Evolution 2.30. You should be able to use Express by editing the Evolution launcher and changing the command to:
```
evolution --express
```Evolution should then launch using the Express interface instead of the default.

---

### Post by 23meg on 2010-09-14
> **Maupertus said:**
> 
On a different note, is it possible to install Evolution Express in a normal Gnome setting? I have tested Unity, didn't like it, but I did like Evolution Express!

Just run it by issuing ```
evolution --express
```

---

### Post by Maupertus on 2010-09-14
Is it correct that the Calendar then isn't accessible? (Although by being so I don't have the jumping window problem)

---

