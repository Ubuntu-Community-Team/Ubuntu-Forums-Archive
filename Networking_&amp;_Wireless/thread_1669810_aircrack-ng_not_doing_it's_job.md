---
title: "aircrack-ng not doing it's job"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-01-18
Hey everyone. 

I am relatively new to wifi cracking and have been attempting to crack my own network, which is protected by WPA.

When i run this command 

aircrack-ng -w '/home/marcom/Desktop/password.lst' -b 00:00:00:00:00:00 psk*.cap

i receive this output. 

                             Aircrack-ng 1.0


                   [00:00:00] 236 keys tested (516.58 k/s)


                       Current passphrase: PR0VIEW!                   


      Master Key     : AE 9B FB 91 23 4B 58 6B 41 85 1D FB BE 99 CB 14 
                       77 74 CB 5C 26 AD C1 DC C7 76 62 AA 03 FB 74 07 

      Transient Key  : 22 11 47 37 41 1D 58 52 AC 70 0E 76 8D 43 E8 C6 
                       6F F8 4B 41 97 04 BE E5 8D 78 DC 48 DF 37 81 DA 
                       DD 79 8C 14 15 57 E5 07 5E F4 C0 C8 8C F2 50 37 
                       B0 58 6D 7D 5E 5B 43 0B A7 66 24 FB EF 2C 78 32 

      EAPOL HMAC     : AE 11 E4 F3 EC A6 9B C2 77 87 26 F0 E5 1B ED D3 

Passphrase not in dictionary 



Quitting aircrack-ng...
-------------------------------------------------

I tried the passprase found and had discovered it was wrong... 

Any ideas or tips to help me thwart this.

---

### Post by wittmaniac on 2011-02-21
> **slashwannabe94 said:**
> Hey everyone. 

I am relatively new to wifi cracking and have been attempting to crack my own network, which is protected by WPA.

When i run this command 

aircrack-ng -w '/home/marcom/Desktop/password.lst' -b 00:00:00:00:00:00 psk*.cap

i receive this output. 

                             Aircrack-ng 1.0


                   [00:00:00] 236 keys tested (516.58 k/s)


                       Current passphrase: PR0VIEW!                   


      Master Key     : AE 9B FB 91 23 4B 58 6B 41 85 1D FB BE 99 CB 14 
                       77 74 CB 5C 26 AD C1 DC C7 76 62 AA 03 FB 74 07 

      Transient Key  : 22 11 47 37 41 1D 58 52 AC 70 0E 76 8D 43 E8 C6 
                       6F F8 4B 41 97 04 BE E5 8D 78 DC 48 DF 37 81 DA 
                       DD 79 8C 14 15 57 E5 07 5E F4 C0 C8 8C F2 50 37 
                       B0 58 6D 7D 5E 5B 43 0B A7 66 24 FB EF 2C 78 32 

      EAPOL HMAC     : AE 11 E4 F3 EC A6 9B C2 77 87 26 F0 E5 1B ED D3 

[SIZE=5]** Passphrase not in dictionary **[/SIZE]



Quitting aircrack-ng...
-------------------------------------------------

I tried the passprase found and had discovered it was wrong... 

Any ideas or tips to help me thwart this.

Four weeks late, but try reading the output. :)

---

### Post by barrieluv on 2011-02-23
> **slashwannabe94 said:**
> 
                   [00:00:00]

I tried the passprase found and had discovered it was wrong... 


In that case, you have unsuccessfully attempted to crack your own password.  That's a good thing, meaning your password won't be cracked by anyone else using a dictionary with only 263 words in it.
To crack your own password, open your wordlist in a text editor, add your own password to the list, save it and then try again.
This should guarantee success.

---

