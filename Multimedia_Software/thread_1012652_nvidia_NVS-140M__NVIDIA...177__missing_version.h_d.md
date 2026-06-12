---
title: "nvidia NVS-140M  NVIDIA...177  missing version.h during installation"
date: 2008-12-16
forum: Multimedia Software
---

### Post by goodidea on 2008-12-16
uname -r
2.6.28-2-generic

During installation new NVIDIA driver (177 build) I bumped to missing '/usr/src/linux/include/linux/version.h' file. So nvidia installer can not proceed. 

How to get missing file?

---

### Post by albandy on 2008-12-16
install the linux kernel source

sudo apt-get install  linux-headers-2.6.27-9 
sudo apt-get install linux-source-2.6.27

---

### Post by goodidea on 2008-12-16
I tried to do:
sudo apt-get install linux-headers-2.6.27-9


have got error message:
Couldn't find package 2.6.27-9


What I need to add in sources.list?

---

### Post by albandy on 2008-12-16
sudo gedit /etc/apt/sources.list
uncomment all deb-src entries (remove the starting character "#")
save file
sudo apt-get update
now you can get the kernel source packages

---

### Post by goodidea on 2008-12-16
nothing to uncomment. see my sources.list file

---

### Post by albandy on 2008-12-17
I thought you was using Intrepid Ibex, ok type "uname -a" to see what kernel version  are  you using.

---

### Post by fareedquraishi on 2008-12-17
E books for all - enjoy 

--------------------------------------------------------------------------------

7 rapidshare_premium_accounts

[http://rapidshare.com/files/17263950...m_accounts.rar](http://rapidshare.com/files/17263950...m_accounts.rar)

4001 Business, Sales and Personal Letters 

Down Load from this link
[http://rapidshare.com/files/17305444...al.Letters.rar](http://rapidshare.com/files/17305444...al.Letters.rar)

Microsoft Access Bible 

There are three parts of this huge book, Microsoft Access From beginners to Expert Level

File: Access Bible.part1.rar
DownloadLink: [http://rapidshare.com/files/17404413...ible.part1.rar](http://rapidshare.com/files/17404413...ible.part1.rar)

File: Access Bible.part2.rar
DownloadLink: [http://rapidshare.com/files/17404965...ible.part2.rar](http://rapidshare.com/files/17404965...ible.part2.rar)

File: Access Bible.part3.rar
DownloadLink: [http://rapidshare.com/files/17405337...ible.part3.rar](http://rapidshare.com/files/17405337...ible.part3.rar)

Formulas and Functions With Microsoft Excel 2003 

File: Formulas and Functions With Microsoft Excel 2003.part1.rar

[http://rapidshare.com/files/17399480...2003.part1.rar](http://rapidshare.com/files/17399480...2003.part1.rar)

File: Formulas and Functions With Microsoft Excel 2003.part2.rar

DownloadLink: [http://rapidshare.com/files/17402749...2003.part2.rar](http://rapidshare.com/files/17402749...2003.part2.rar)

File: Formulas and Functions With Microsoft Excel 2003.part3.rar

DownloadLink: [http://rapidshare.com/files/17403228...2003.part3.rar](http://rapidshare.com/files/17403228...2003.part3.rar)

File: Formulas and Functions With Microsoft Excel 2003.part4.rar LAST PART

File: Formulas and Functions With Microsoft Excel 2003.part4.rar

DownloadLink: [http://rapidshare.com/files/17403388...2003.part4.rar](http://rapidshare.com/files/17403388...2003.part4.rar)

----------------------------------------------------------------------------------------------

KFC AUTHENTIC RECIPES

Mc DONALDS INCLUDES ALL THESE
Big Mac®
Arch Deluxe®
Big X-tra®
Breakfast Burrito
Cheeseburger
Chicken Fajitas
Chicken McNuggets®
Egg McMuffin®
Filet~o~Fish®
French Fries
Hamburger
McChicken®
McD.L.T.®
McRib® Sandwich
Milkshakes
Quarter Pounder®
Sweer & Sour Dipping Sauce

200 PIZZA RECIPE BOOK

VEDIC MATHEMATIC SECRET

File: Mc Donalds and KFC Recipes.rar
DownloadLink: [http://rapidshare.com/files/17403824...FC_Recipes.rar](http://rapidshare.com/files/17403824...FC_Recipes.rar)

--------------------------------

BODY LANGUAGE DICTIONARY 

[http://rapidshare.com/files/17398536...Dictionary.pdf](http://rapidshare.com/files/17398536...Dictionary.pdf) 

-------------------------------------------------------

child reading
Dream Psychology
inequal justice
Homeopathy Pro v1.0.0 build 51010 w fix

All in one Link - Enjoy

File: Homeopathy.rar
DownloadLink: [http://rapidshare.com/files/173971588/Homeopathy.rar](http://rapidshare.com/files/173971588/Homeopathy.rar)

=====================

1000 hacking tutorials-The Best of 2008 

[http://rapidshare.com/files/17305827..._of__2008_.rar](http://rapidshare.com/files/17305827..._of__2008_.rar)
====================================

The Emotionally Intelligent Manager - Jossey Bass
Becoming a Strategic Leader Your Role in Your Organizations Enduring Success - Wiley
Everybody Wins The Story and Lessons Behind RE MAX
Getting An Investing Game Plan Creating It Working It Winning It -John Wiley&Sons
living the brand
Crunch Point The 21 Secrets to Succeeding When It Matters Most
Leadership Secrets of the Worlds Most Successful CEOs-Dearborn Financial 
Publishing
Customer_Once_Client_Forever
Hotel_Front_Office_Management_3rd_Edition_-_John_Wiley_and_Sons
The_Essentials_of_the_New_Workplace_A_Guide_to_the _Human_Impact_of_Modern_Working_Practices

these all books are in these two links, Lots to come

[http://rapidshare.com/files/172962944/ebooks1.rar](http://rapidshare.com/files/172962944/ebooks1.rar)
[http://rapidshare.com/files/172962945/ebooks_2.rar](http://rapidshare.com/files/172962945/ebooks_2.rar)

================================

4001 Business, Sales and Personal Letters 


Down Load from this link
[http://rapidshare.com/files/17305444...al.Letters.rar](http://rapidshare.com/files/17305444...al.Letters.rar)

---

