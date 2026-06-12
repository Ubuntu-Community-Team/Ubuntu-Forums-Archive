---
title: "Installing openoffice in Natty Narwhal - Slow Libreoffice Calc"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by frncz on 2011-03-07
I find that LibreOffice Calc is very slow when I handle spreadsheets with many lines (e.g 30,000), both in Maverick and in Natty. Even with 4,000 lines, Libroffice Calc is useless. Openoffice 3.2.1 seems to handle such files very well.
I am trying to install openoffice in Natty to resolve this problem, but can't. Somehow there are transition files that seem to translate openoffice installtion to libreoffice installation.
Can I overrule this, somehow? dpkg and synaptic did not work. Synaptic shows openoffice as already installed, but it isn't!

It would of course be better if Libreoffice Calc worked with large data files?
Thanks for your help

---

### Post by nomko on 2011-03-07
First remove LibreOffice completly. Search for a package which ends with -data or -common. Slect that file for complete remove. It will select all packages who's dependent on that -common or -data file. Check if everything is selected for complete removal. Press the Apply button (or OK button). After that you can install OpenOffice.
 
Hope it works this way!

---

### Post by frncz on 2011-03-07
> **nomko said:**
> First remove LibreOffice completly. Search for a package which ends with -data or -common. Slect that file for complete remove. It will select all packages who's dependent on that -common or -data file. Check if everything is selected for complete removal. Press the Apply button (or OK button). After that you can install OpenOffice.
 
Hope it works this way!

Good idea. will try

Thanks

Mike

---

### Post by oldfred on 2011-03-07
Ok, now the old part of oldfred comes out.

When starting to do budgets on a spread sheet, I found SuperCalc could only handle about two pages of green bar paper, both in number of columns & rows. I converted to a dBase program and it did require some planning & programming to make it work. 

But I realized that any data that was more than a couple of pages started to become too large for managing in a spreadsheet. While newer software allowed it, would would look for ways to use a database instead of spreadsheet for large data sets. I did use 1-2-3 and then Excel a lot but also dBase, then Access & now SQLite.

It may be time to look at a database for your data if it is that large.

---

### Post by frncz on 2011-03-08
> **oldfred said:**
> Ok, now the old part of oldfred comes out.

When starting to do budgets on a spread sheet, I found SuperCalc could only handle about two pages of green bar paper, both in number of columns & rows. I converted to a dBase program and it did require some planning & programming to make it work. 

But I realized that any data that was more than a couple of pages started to become too large for managing in a spreadsheet. While newer software allowed it, would would look for ways to use a database instead of spreadsheet for large data sets. I did use 1-2-3 and then Excel a lot but also dBase, then Access & now SQLite.

It may be time to look at a database for your data if it is that large.
Thanks oldfred, but it seems to be quite a learning curve. I am used to spreadsheets, and to being able to look at all the data easily, without writing code. Are there spreadsheet-like front-ends for databases? 

I have also used dBase (in DOS) and Access for text data, essentially to replace index card systems, but not for fitting models to number data that is spewed out of our experimental rigs at 10kHz. 

Advice welcome as I am happy to learn.

---

### Post by frncz on 2011-03-08
> **frncz said:**
> Good idea. will try

Thanks

Mike

Well, I removed Libreoffice. I could not re-install openoffice from synaptic as somehow Libreoffice gets re-installed.
I downloaded openoffice .DEBS from the openoffice website and successfully installed openoffice using 'sudo dpkg -i -R *'

However, I find that openoffice Calc has gone as slow as libreoffice for my large spreadsheets! and is also unusable under Natty Narwhal Alpha3.

So this may be a Natty problem, and not a Libreoffice issue.

---

### Post by Harry33 on 2011-03-08
> **frncz said:**
> Well, I removed Libreoffice. I could not re-install openoffice from synaptic as somehow Libreoffice gets re-installed.
...


The latest Openoffice packages in Natty repos are transitional packages to install Libreoffice.

---

### Post by nomko on 2011-03-08
> **frncz said:**
> So this may be a Natty problem, and not a Libreoffice issue.
 
What are the specs of your computer? Do you have enough memory?

---

### Post by frncz on 2011-03-08
> **Harry33 said:**
> The latest Openoffice packages in Natty repos are transitional packages to install Libreoffice.

Yes, exactly. This is quite confusing. It makes it hard to choose between openoffice and libreoffice.

---

### Post by frncz on 2011-03-08
> **nomko said:**
> What are the specs of your computer? Do you have enough memory?

I have 2Gb memory. The biggest spreadsheet is 6Mb. No problem at all in maverick with openoffice, only in natty. On the otherhand, Gnumeric handles the files fine in natty!

---

### Post by nomko on 2011-03-08
> **frncz said:**
> I have 2Gb memory. The biggest spreadsheet is 6Mb. No problem at all in maverick with openoffice, only in natty. On the otherhand, Gnumeric handles the files fine in natty!
 
What kind of spreadsheet is it? What do you do with it? Maybe there's something in the spreadsheet which slow downs or not workable for OpenOffice and LibreOffice. But on the other hand it is strange that Gnumeric do handle that file without any problems.

---

### Post by Hagar Delest on 2011-03-08
Try also to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

