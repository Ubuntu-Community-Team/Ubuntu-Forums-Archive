---
title: "Rule with hebrew in SQL"
date: 2009-05-07
forum: Mythbuntu
---

### Post by reformy on 2009-05-07
Hi
I have mythbuntu 8.10 installed at home on an old (4yrs...) P4 3Ghz machine, connected to a lovely 32" LG Scarlet.
The whole system works excellent with Hebrew, and the titles are correctly displayed. I can record episodes of an Hebrew-titled show with no problems.

The problem:
I'm trying to create a rule that will record all showings with an Hebrew word in the title:
program.title like '%&#1499;&#1493;&#1499;&#1489;&#1497;&#1501;%'
When I hit "test", it shows me all the relevant shows. BUT - when I hit "record" to activate the rule - I see nothing in the "upcoming recordings".
Rules with English words work well.

Any ideas? Is it simply a bug?

Thanks,
Yair

---

### Post by mathog on 2009-05-07
> **reformy said:**
> 
program.title like '%&#1499;&#1493;&#1499;&#1489;&#1497;&#1501;%'


This could be bug in the logic related to handling a R->L
language. What happens if you enter the name with the letters in reverse order?

---

### Post by reformy on 2009-05-12
> **mathog said:**
> This could be bug in the logic related to handling a R->L
language. What happens if you enter the name with the letters in reverse order?

thanks for your answer.

I thought about that (great minds think alike!) and tried only one letter, same behavior.

---

### Post by reformy on 2009-05-13
> **mathog said:**
> This could be bug in the logic related to handling a R->L
language. What happens if you enter the name with the letters in reverse order?

So, is it a bug? Should I report it in some bugzilla of Mythbuntu?

---

### Post by ian dobson on 2009-05-13
Hi,

Maybe you need to use the collate function to tell mysql what format to use, something like:-

SELECT *
 FROM t1
 WHERE k LIKE _latin1 'Müller' COLLATE latin1_german2_ci;


See:-
[http://dev.mysql.com/doc/refman/5.1/en/charset-charsets.html](http://dev.mysql.com/doc/refman/5.1/en/charset-charsets.html) 

I imagine the problem is that mysql is miss interpreting the select command text coding (UTF-8?) and the database character coding.

Regards
Ian Dobson

---

### Post by reformy on 2009-05-14
> **ian dobson said:**
> Hi,

Maybe you need to use the collate function to tell mysql what format to use, something like:-

SELECT *
 FROM t1
 WHERE k LIKE _latin1 'Müller' COLLATE latin1_german2_ci;


See:-
[http://dev.mysql.com/doc/refman/5.1/en/charset-charsets.html](http://dev.mysql.com/doc/refman/5.1/en/charset-charsets.html) 

I imagine the problem is that mysql is miss interpreting the select command text coding (UTF-8?) and the database character coding.

Regards
Ian Dobson

I tried addig "COLLATE hebrew_general_ci" and got:
```
COLLATION 'hebrew_general_ci' is not valid for CHARACTER SET 'latin1'
```

I think that since the "test" option works, it is simply a bug in the recording option, no?

---

### Post by reformy on 2009-05-26
Where can I report this bug?

---

