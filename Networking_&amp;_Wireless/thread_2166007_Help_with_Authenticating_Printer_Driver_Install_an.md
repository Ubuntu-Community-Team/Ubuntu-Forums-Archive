---
title: "Help with Authenticating Printer Driver Install and Printer Problems"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by PartyClass on 2013-08-07
So I have been trying to set up a printer on my Ubuntu laptop. Note that it is shared with a windows 8 computer. I click the icon in the top right corner and select printers. Then in the window select add printer. It asks to authenticate fetching the deice list, it doesn't auto-fill my name like usual. I put my username and password in (yes I am admin), but it says its incorrect. I press cancel and it doesn't seem to do much. Using the windows 8 computer I find the host for the printer which is 'HPE6DF3', it finds the printer OK. It asks me to enter my password, though this time it fills everything out (except password) and has a space for domain. It logs in fine. I find my printer in the database (HP Officejet j6400). It says that the printer has some addition software I can install, something called Duplexer. Whether I check it or not it leads to another page asking what I want to name it. I press accept and it asks me to authenticate. It won't accept my username and password. I imagine it is not actually looking for my actual user password and maybe something with the network. So how do I get it to authenticate?

---

### Post by gordintoronto on 2013-08-07
To authenticate, just enter your password.

---

### Post by Mark Phelps on 2013-08-08
In your text, you mentioned "domain".  Is this laptop connected to a Windows domain? IF so, that's going to pose serious problems sharing a printer connected to this laptop.

---

