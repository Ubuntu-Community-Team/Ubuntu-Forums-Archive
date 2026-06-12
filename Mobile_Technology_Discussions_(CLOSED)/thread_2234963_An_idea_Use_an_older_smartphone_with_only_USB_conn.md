---
title: "An idea: Use an older smartphone with only USB connectivity as a password locker"
date: 2014-07-18
forum: Mobile Technology Discussions (CLOSED)
---

### Post by andrew_smith6 on 2014-07-18
I need a device to:
[LIST]
[*]Hold passwords and other personal information that I can read and type into another device. (Yes it is slow and error-prone. But it is secure from everything except key-loggers, and can be used everywhere without dependency on net connection, third-party software, or trust of some cloud provider.)
[*]Secure this information from loss or theft should the device be lost, destroyed, or stolen.
[*]Be self contained and the information be easy to view and edit on the device.
[/LIST]
The device I have been using for this is an old Palm m515 I carry wherever I go, but it is at the end of its working life. The modern equivalent is a smartphone. It is pocketable, has a screen, you can type into it and has a wired physical connection to back up through. It is also has a CPU powerful enough so that with the right software it could do on-the-fly encryption so the information is kept on the device in a safe manner, yet with the right credentials (master password kept between the ears) can edit and display it. But there are many more vectors for attack on such a device, both from within the device software itself, and through mobile data/WiFi/Bluetooth, things the M515 was too primitive for, or just didn't have. Enter Ubuntu Touch. Now it seems to me Touch is at a point in its development where it will run well enough on say a Samsung S3 to be stable, but can knobble the radio communication part of the device sufficiently to remove any possibility of them to be a security threat vector. There would also need to be the ability to view the encrypted file on a PC should the device be unavailable, but this would only be used in emergency as there is the possibility of attack on the master password via a key-logger on the PC. The question is: Is there software that will provide the encryption described with the use-case of password entry first, then view, edit, save, and back up the encrypted info through the USB to PC and cloud?

---

### Post by tgalati4 on 2014-07-18
How much data are we talking about?

Evernote can encrypt single note pages, but not notebooks--nor is there any inclination to include that feature:  [https://discussion.evernote.com/topic/36764-encrypt-a-whole-notebook/](https://discussion.evernote.com/topic/36764-encrypt-a-whole-notebook/)

Why would you carry around a smartphone for this purpose? You could simply carry a USB stick with your encrypted data on it and just use the computer you are on to decrypt it and edit it.  There is some talk about adding encryption to *[zim]("http://zim-wiki.org/index.html")*, a simple wiki-style notebook editor.  You could also write a script to perform the steps you described above to insert USB stick, decrypt, open zim, perform your edits, save and close zim, encrypt file, eject USB stick.

Within *zim* is a script facility to perform whatever you want:  [https://github.com/jaap-karssenberg/zim-wiki/wiki/Custom-tools](https://github.com/jaap-karssenberg/zim-wiki/wiki/Custom-tools)

Data entry on a smartphone (especially a Galaxy S3) is a pain without a bluetooth keyboard.  Now you have to carry a keyboard and a phone.  If you have a smartphone, then just use the evernote app.  It works well, but data entry is a pain, unless you like to speak into it and correct a lot of errors--especially technical stuff.

How much of your data needs encryption?  20%, 50%, 100%

---

### Post by andrew_smith6 on 2014-07-20
Firstly, thank you for your reply.
> **tgalati4 said:**
> > How much data are we talking about?
Not much, mostly a comma delimited list of services, username, password. There would be perhaps 20 services in 4 catagories.

[QUOTE]Evernote can encrypt single note pages, but not notebooks--nor is there any inclination to include that feature:  [https://discussion.evernote.com/topic/36764-encrypt-a-whole-notebook/](https://discussion.evernote.com/topic/36764-encrypt-a-whole-notebook/)
Nor should I imagine, on smartphones. 

> Why would you carry around a smartphone for this purpose? You could simply carry a USB stick with your encrypted data on it and just use the computer you are on to decrypt it and edit it.  There is some talk about adding encryption to *[zim]("http://zim-wiki.org/index.html")*, a simple wiki-style notebook editor.  You could also write a script to perform the steps you described above to insert USB stick, decrypt, open zim, perform your edits, save and close zim, encrypt file, eject USB stick.

These passwords will be used for locked-up work PC's, maybe at a kiosk, at an ATM, lots of places where the operating system will either not run the contents of a USB or will be a threat to it.

> Within *zim* is a script facility to perform whatever you want:  [https://github.com/jaap-karssenberg/zim-wiki/wiki/Custom-tools](https://github.com/jaap-karssenberg/zim-wiki/wiki/Custom-tools)
I shall investigate.

> Data entry on a smartphone (especially a Galaxy S3) is a pain without a bluetooth keyboard.  Now you have to carry a keyboard and a phone.  If you have a smartphone, then just use the evernote app.  It works well, but data entry is a pain, unless you like to speak into it and correct a lot of errors--especially technical stuff.

Ah yes I agree it is PAINFUL to enter and edit, but once entered it will only change every few months at the most, and then only for a few characters. 

> How much of your data needs encryption?  20%, 50%, 100%

100%, but it is really a relatively tiny amout of data. 
Thank you for your time and suggestions. :)

---

### Post by tgalati4 on 2014-07-20
Sounds like you need a Password Vault:  [https://play.google.com/store/search?q=password+vault&c=apps](https://play.google.com/store/search?q=password+vault&c=apps)

There are several hundred available for Android.  Most are free.  You can read the reviews and determine if they meet your security requirements.  With an Android phone, you can use "Airplane Mode" to turn off 3G, wireless and bluetooth.  To add security, you can store your passwords, then carry a keychain with a tag engraved as such:

1.  1385
2.  2853
3.  3902
4.  2938
.
.

Then store the key number at the end of your password for a given service in the password vault.  When you use your password at an ATM, open the phone vault, type in the password, then type in the last 4 numbers (or letters) based on the key number.  As long as you have both your keys and your phone, you can build your passwords in the field.  If you lose either your keys or your phone, then your passwords are broken.  If you lose both at the same time, then use a paper backup because you will need to change all of your passwords.

For example:

Phone Vault:

Swindler's Bank 38d849902d**4**

Since 4 is the last number, your full password is:

38d849902d**2938**

You don't need a smartphone for this.  You could simply put your accounts on a business card with the partial passwords and get a keychain engraved with 10 or so keys.  Just don't lose your keys and your wallet!

Need addtional complication?  You can use the front and back of the partial password.  The first digit (3 in this case) could be expanded as well:

**3902**8d849902d**2938**

I'm sure there are other [methods]("http://www.wikihow.com/Keep-Your-Debit-Card-Number-%28PIN%29-Safe") that folks use.

---

### Post by david253 on 2014-07-21
Wow, that is really clever...you would only know what it means and can be safe carrying this round without writing passwords down somewhere obvious! Great idea!

---

### Post by tgalati4 on 2014-07-21
Newer bank ATM's can handle a 16-digit PIN (not all so check before changing your passwords!).

You could memorize your ATM's original 4-digit key (perhaps 2943)

Then look at your keychain with 10 engraved, 4-digit numbers

0. 1390
1.  3866
2. 2296
3. 0092
4. 7295
5. 2209
6. 1964
7. 2548
8. 1274
9. 2371

You now expand your 4-digit pin to 16 digits.  So 2943 becomes:

2296 2371 7295 0092

Now you only have to store your accounts and key-generators on a single, printed card or in an encrypted file or both.

I just used numbers because ATM's only accept numbers, but you can have extra keys with letters and symbols to generate passwords for web accounts.

10.  OmkeOnWon2
11. RhadInCoj5
12.  otAtAigsIj0
13  BirpusEawd9
14  Mobbysdebad3
15.  masnOon3

(These were generated with *agp*.)

Now store your accounts:

Ubuntu SSO  12 15 6
Facebook 10 13 11 2
Twitter 14 12

---

