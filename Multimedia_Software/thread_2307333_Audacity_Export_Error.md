---
title: "Audacity Export Error"
date: 2015-12-24
forum: Multimedia Software
---

### Post by Elijah_Duffy on 2015-12-24
I have edited some audio using Audacity, but whenever I try to export the audio to a .mp3 or .ogg file, I get a popup error window saying "An assertion failed!" (see attached picture). Once I get that popup, no matter what I do I am virtually doomed. If I click the x, Audacity crashed. If I click Stop or Continue, Audacity crashes.

Any help would be greatly appreciated.

---

### Post by Bucky Ball on 2015-12-24
*Thread moved to **Multimedia Software**.*

Which release of Ubuntu are you using? Do you have ubuntu-restricted-extras installed? What file format is the source audio in (the original audio file you are editing)?

---

### Post by mc4man on 2015-12-25
Error is typical of altering the metadata, don't you have a 'Continue' choice on pop up?
Otherwise try not having the metadata editor open on export (- Edit > Preferences > Import/Export > obvious

---

### Post by Elijah_Duffy on 2016-01-12
I am using Ubuntu 15.10. As far as I know, I don't have any ubuntu-restricted-extras installed. My source audio is ogg.

I do have a continue choice when I get my error, but Audacity just crashes anyway. I will note that I did completely fill out the metadata including adding another field. Since you mention it, I will have to try not entering metadata, as well as not adding another field. Thanks for your input!

---

### Post by Autodave on 2016-01-14
I would definitely install both "ubuntu restricted extras" and "ubuntu restricted add-ons".  Providing, of course, you are not in a country where that is prohibited.

---

### Post by yoshii on 2016-01-14
I would do a "sudo purge audacity" (to remove audacity and all of it's settings), and then do a "sudo install audacity" to install audacity if it's available from the PPA's.  Otherwise follow the install instuctions from the Audacity website. Then you will have to manually reset up all of the preferences and settings for Audacity from within Audacity.

---

