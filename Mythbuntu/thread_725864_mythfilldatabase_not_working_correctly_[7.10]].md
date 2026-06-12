---
title: "mythfilldatabase not working correctly? [7.10]]"
date: 2008-03-16
forum: Mythbuntu
---

### Post by pixeldotz on 2008-03-16
months back i had followed the instructions in the wiki to install mythtv (backend and mythweb) manually into ubuntu 7.10.

i then used zap2xml to generate my tv scrapings and imported them into mythtv with

> mythfilldatabase --file 1 -1 /xmltv.xml

worked fine for months with the manual install.

after hearing about mythbuntu i decided to give it a shot and installed 7.10

everything works fine and i can setup recordings and everything is awesome.

except it no longer takes my xmltv.xml file. running it the same the terminal displays that it has found programs and everything goes fine. however, mythweb and the frontend do not show anything at all.

numerous re-installs have resulted in the same error. here's a snip from the xmltv.xml file.

> 
	<channel id="I18151.labs.zap2it.com">
		<display-name>58 TOONP</display-name>
		<display-name>58</display-name>
		<display-name>TOONP</display-name>
	</channel>
	<channel id="I11007.labs.zap2it.com">
		<display-name>63 NIKP</display-name>
		<display-name>63</display-name>
		<display-name>NIKP</display-name>
	</channel>

does anyone know whats happening or if something i'm doing is wrong maybe?

 (i can't test out 8.04. i've been trying to download and burn it for hours; but everytime it starts installing i get install errors. dirty disk msgs. ive downloaded and burned it about 5 times and still no go. 7.10 installs on the first try everytime.)

---

### Post by foxbuntu on 2008-03-18
Did you install XMLTV in Mythbuntu 7.10, it is not preinstalled unless you chose it in the setup.

---

### Post by pixeldotz on 2008-03-20
i honestly cannot remember.

is there a way to install it without having to redo the entire box?

---

### Post by oldHat on 2008-06-13
Have you solved this yet?  I just found some new releases on the zap2xml website, necessary because of changes as zap2it.  Solved all *my* new problems.

#

*

# 2008-02-15

    * Updated parser for zap2it's new "new/live/hd" tags 

# 2008-03-11

    * Updated program description cookie to match zap2it's new one 

# 2008-05-25

    * Updated to handle zap2it's latest website changes 

# 2008-05-29

    * Handle channel numbers with "." in them

---

