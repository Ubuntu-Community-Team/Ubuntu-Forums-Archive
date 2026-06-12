---
title: "[SOLVED] Help with Custom Record syntax"
date: 2008-05-13
forum: Mythbuntu
---

### Post by kyfehr on 2008-05-13
I am in need of some help. I have been searching the web and the forum but can't find a site that really explains the syntax used for the power search in the Custom Record.

I have been using very basic searches but I need to create a search to find all programs like this but NOT like this

this is what I have written:
program.title LIKE '%Biggest Loser%'
AND program.title NOT '%Australia%'

and when I save it I get this error:
Error:
There is an error in your custom SQL query:

check the manual that corresponds to your MySQL server version for the right syntax to use near ''%Australia%'' at line 2 [#1064]

I have tried to find the syntax to exclude something but haven't been able to. Help would be great.

kyfehr

---

### Post by kyfehr on 2008-05-14
Is this not possible? does anyone have a source they can link me to?

My continued searches have not been helpful. If this simply not possible?

Thanks.

---

### Post by gazer22 on 2008-05-14
I'm no expert on this, but it looks like you want "NOT LIKE" on the second line, not just "NOT:"

> **kyfehr said:**
> ```

program.title LIKE '%Biggest Loser%'
AND program.title NOT [COLOR="Red"]**LIKE**[/COLOR] '%Australia%'
```


---

### Post by kyfehr on 2008-05-14
Well if it is possible to feel like a total idiot. In all my attempts that specific phrasing didn't occure to me. Thank worked - as far as I can see. Thanks for the help.

---

