---
title: "Thunderbird - Main Screen Text Very Small"
date: 2021-08-13
forum: MINT
---

### Post by michaelmacho on 2021-08-13
Hello Everyone - 

Note:  Image Attached.


I am new to using Linux as my daily driver OS. Just 4 days ago Windows took a crap with an update and Microsoft did not call for 4 days. I finally got so frustrated as a Microsoft Partner that I formatted my machine and installed Linux. I had been thinking about doing this for some time and watched many You Tube videos on the best way to do this and make life easy again. Anyways I am on day 6 of using Mint Linux with Ubuntu and I have managed to accomplish a lot.


I am running Thunderbird with a number of nice Ad On's for my email.  I am really sorry for such a dumb question.  I cant seem to make the main screen of the various email folders, inbox, sent mail etc **text larger.  It is quite small and it would be nice not to have to strain my eyes just to see it.  **

**When I click an actual email message I am able to increase the zoom % but not in the main box such as the inbox.  I attached a picture of by junk mail as an example of how small the text is. **

**I have not changed the resolution settings on the computer as this is the only program affected by the screen text size.  **

The email server is running Microsoft Exchange on Prem version with the latest updates and version of Exchange.  

**Any thoughts?  **

---

### Post by wildmanne39 on 2021-08-14
Moved to the Mint sub-forum.

---

### Post by michaelmacho on 2021-08-14
Thank you ):P

---

### Post by ajgreeny on 2021-08-14
There are settings in the thunderbird preferences that you can set to increase text size, but you can also temporarily change it with Ctrl+, just like Firefox, if you use that.

---

### Post by norobro on 2021-08-14
This worked for me in Thunderbird 78.13.0:

[LIST]
[*]From the main toolbar select Edit -> Preferences or press the hamburger icon (upper right) and select preferences
[*]Scroll to the bottom of the screen and push the "Config Editor ..." button
[*]In the search bar enter: font.size.systemFontScale
[*]Double click on the item and input a larger integer (my default was 100)
[*]click "OK", close the window, and close TBird.
[/LIST]
The change took effect on restart.

HTH

---

### Post by michaelmacho on 2021-08-14
Thank you - This worked perfectly.  Do you know what the preference name is for font change of actual font.  The default font is not great.  This would allow me to change the font of the front screen.

[COLOR=#000000][INDENT]".....but you can also temporarily change it with Ctrl+, just like Firefox, if you use that"[/INDENT]
[/COLOR]

Thank you I was aware of this option.  No this does not work on the main screen.  only within an email and as you said only temporary.  NoroBro ID instructions helped me to solve the issue.  Thank you

---

