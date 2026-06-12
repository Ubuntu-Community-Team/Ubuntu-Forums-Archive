---
title: "Iwant to hide my wireless passwords"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by forsubhi on 2012-06-19
I want to hide my wireless passwords with user password 
can I do that ?

---

### Post by poolet on 2012-06-20
> **forsubhi said:**
> I want to hide my wireless passwords with user password 
can I do that ?

what exactly you mean with that?? something like a second password if the
first one authenticate by someone to have onother?? 

just make your wireless, AES encryption(instead of TKIP), use WPA2 and make your SSID hidden!!!

---

### Post by CharlesA on 2012-06-20
Hiding your SSID doesn't do anything for security btw.

@OP: Do you mean you want to hide the passphrase you use for connecting to your wireless?

---

### Post by forsubhi on 2012-06-20
> @OP: Do you mean you want to hide the passphrase you use for connecting to your wireless?

yes , I Do .

---

### Post by sammiev on 2012-06-20
I wondered about that myself as if you go into Network Settings you can view the saved password for connecting to the wireless using wpa2 or any other.

---

### Post by SeijiSensei on 2012-06-20
On Kubuntu, the wireless passphrase is stored in the [KDE Wallet]("http://utils.kde.org/projects/kwalletmanager/").  You should have been prompted about using the wallet the first time you entered the password.  It's easy to skip over that function and disable using the wallet by mistake.  The easiest solution is to delete the existing wallet and start over.

Go to System Settings > Account Details > KDE Wallet.  Make sure the Wallet is enabled, then click the Launch Wallet Manager button.  You'll see a window open with your current wallet(s); there will probably just be one.  Right-click the wallet and delete it.  Close the manager.

Now click on the Network Manager icon in the System Tray and disconnect from the wifi network.  The easiest way to do that is to uncheck the "Enable Wireless" box at the bottom.  Now recheck the box, and you should be prompted to use the wallet to store the wifi passphrase.  Choose "Allow Always" then enter your password.  It will be encrypted and stored in the wallet.  From then on, you'll be automatically reconnected without needing to enter the passphrase.

As I recall you'll also be prompted to enter a password for the Wallet itself.  I always skip this by hitting Enter to create a blank Wallet password.  If you're more paranoid than me, or if the possibility exists that someone else might use your computer and knows your login password, then you might prefer having a Wallet password.  You'll have to enter the password each time you log into your desktop before it will connect to the wifi network.

---

