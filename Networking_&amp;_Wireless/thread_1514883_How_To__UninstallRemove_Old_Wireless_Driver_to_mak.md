---
title: "How To:  Uninstall/Remove Old Wireless Driver to make way for New Driver (RTL8191SE)?"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by u2rcrazy on 2010-06-21
[SIZE=4]**How To:  Uninstall/Remove Old Wireless Driver to make way for New Driver (RTL8191SE)?**[/SIZE]

[CENTER]Here's the new driver:  
[/CENTER]
 
I have been having trouble with my wireless connection intermittently disconnecting and reconnecting repeatedly (sometimes every couple of seconds).  I posted a thread about this here on Ubuntu Forums titled:  [**Ubuntu 10.45 & NetworkManager Applet 8.0:  Connects &  Disconnects Frequently**]("http://ubuntuforums.org/showthread.php?t=1508501").  I also emailed Realtek and requested help and received the following email:[INDENT]    [SIZE=-1]** From:  roger_liang <roger_liang@realtek.com> **[/SIZE]   [SIZE=-1]** Wed, Jun 16, 2010 at 8:39 PM **[/SIZE]   [SIZE=-1]  To: _ME_
 [/SIZE]      [SIZE=-1]   [FONT=Times New Roman][SIZE=2][COLOR=black]Dear Sir / Madam,[/COLOR][/SIZE][/FONT]
 
 [FONT=Times New Roman][SIZE=2][COLOR=black]Thanks for your mail.[/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black]Please find the latest RTL8191SE  Linux driver source in the attachment.[/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][COLOR=Red][SIZE=2]You should clear previous drive  first after you install this driver source.[/SIZE][/COLOR][/FONT][COLOR=Red]
[/COLOR]  [FONT=Times New Roman][COLOR=Red][SIZE=2]The previous driver will be  stored within /lib/modules/2.6.XXX/kernel/driver/staging.[/SIZE][/COLOR][/FONT][COLOR=Red]
[/COLOR]  [FONT=Times New Roman][COLOR=Red][SIZE=2]Please remove "r8192se_pci.ko" file.[/SIZE][/COLOR][/FONT][COLOR=Red]
[/COLOR]  [FONT=Times New Roman][COLOR=Red][SIZE=2]You could execute find-name "r8192se_pci.ko" in /lib/modules/2.6.XXX to check it’s clear properly.[/SIZE][/COLOR][/FONT]
 [FONT=Times New Roman][COLOR=Purple][SIZE=2]And then, install this driver  source as below steps. Don’t forget to unzip this package before you install it.[/SIZE][/COLOR][/FONT][COLOR=Purple]
[/COLOR]  [FONT=Times New Roman][COLOR=Purple][SIZE=2]1. sudo su[/SIZE][/COLOR][/FONT][COLOR=Purple]
[/COLOR]  [FONT=Times New Roman][COLOR=Purple][SIZE=2]2. make[/SIZE][/COLOR][/FONT][COLOR=Purple]
[/COLOR]  [FONT=Times New Roman][COLOR=Purple][SIZE=2]3. make install[/SIZE][/COLOR][/FONT][COLOR=Purple]
[/COLOR]  [FONT=Times New Roman][COLOR=Purple][SIZE=2]4. reboot[/SIZE][/COLOR][/FONT][COLOR=Purple]
[/COLOR]  [FONT=Times New Roman][COLOR=Purple][SIZE=2]5. ./wlan0up or ./wlan1up[/SIZE][/COLOR][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black]If you have any questions, feel  free to let us know.[/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black]Thanks.[/COLOR][/SIZE][/FONT]
 
  [FONT=Times New Roman][SIZE=2][COLOR=black]Best Regards,[/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black]Roger_Liang[/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black]Realtek Semiconductor Corp.[/COLOR][/SIZE][/FONT]
 ____________________________________________
  
**To**[/SIZE][SIZE=-1]**:  **[/SIZE][SIZE=-1]_ME_[/SIZE]   [SIZE=-1]** Wed, Jun 16, 2010 at 11:36 PM **[/SIZE]   [SIZE=-1]  To: roger_liang <roger_liang@realtek.com> 
 [/SIZE]      [SIZE=-1][SIZE=1][COLOR=#888888]

[/COLOR][/SIZE] [/SIZE]       [SIZE=-1]** FROM:  roger_liang <roger_liang@realtek.com> **[/SIZE]   [SIZE=-1]** Wed, Jun 16, 2010 at 11:44 PM **[/SIZE]   [SIZE=-1]  To: [SIZE=-1]_ME_[/SIZE] 
 [/SIZE]      [SIZE=-1]   [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]Dear Sir,[/COLOR][/COLOR][/SIZE][/FONT]
 
 [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]Yes, you should  remove the older driver then install the new one.[/COLOR][/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]Please just follow  our description to configure driver source. Thanks.[/COLOR][/COLOR][/SIZE][/FONT]
[COLOR=#550055] 
  [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]Best Regards,[/COLOR][/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]Roger_Liang[/COLOR][/COLOR][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]Realtek  Semiconductor Corp.[/COLOR][/COLOR][/SIZE][/FONT]
 [/COLOR][/SIZE][SIZE=-1]____________________________________________

[/SIZE][SIZE=-1]  **[FONT=Tahoma][SIZE=2][FONT=Tahoma][B]From:**[/FONT][/SIZE][/FONT][/B][SIZE=-1]_ME_[/SIZE]
[FONT=Tahoma][SIZE=2][FONT=Tahoma] **[B]Sent:**[/B] Thursday, June 17,  2010 2:36 PM
**[B]To:**[/B] Roger Liang
**[B]Subject:**[/B] Re: Ubuntu 10.45  & NetworkManager Applet 8.0: Connects & Disconnects Frequently[/FONT][/SIZE][/FONT]
 [/SIZE] [SIZE=-1]**To:** roger_liang <roger_liang@realtek.com> 
 [/SIZE]      [SIZE=-1]Roger,

Thank you for your response[IMG]https://mail.google.com/mail/e/360[/IMG]  Do you have and automatic  uninstaller for "[FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]r8192se_pci.ko[/COLOR][/COLOR][/SIZE][/FONT]"  and a automatic installer for [FONT=Times New Roman][SIZE=2][COLOR=black][COLOR=black]RTL8191SE[/COLOR][/COLOR][/SIZE][/FONT][IMG]https://mail.google.com/mail/e/361[/IMG]  [COLOR=Red]I [COLOR=DarkOrange]performed a file search for  "[/COLOR][/COLOR][FONT=Times New Roman][COLOR=DarkOrange][SIZE=2]r8192se_pci.ko[/SIZE][/COLOR][/FONT][COLOR=DarkOrange]" and found three files installed (see attached screenshot for a  description of where they're are it).  I attempted to uninstall them  all, but Ubuntu said I didn't have permission (see attached screen shots  for system messages).[/COLOR] [COLOR=DarkGreen]I then tried to use the terminal to delete the  files, but I couldn't fine the "lib" folder (see "Terminal" screen shot for  transcript of what transpired).  [/COLOR]

Roger, can you help me on this?  I'm at a loss on what to do[IMG]https://mail.google.com/mail/e/35F[/IMG]

Sincere,
Bob Marly[IMG]https://mail.google.com/mail/e/1E3[/IMG][SIZE=1][COLOR=#888888][Quoted text hidden][/COLOR][/SIZE]
[/SIZE] 
[SIZE=1][ATTACH]161116[/ATTACH][/SIZE]  [ATTACH]161117[/ATTACH]  [ATTACH]161118[/ATTACH]  [ATTACH]161119[/ATTACH]
[SIZE=-1]____________________________________________[/SIZE]
[/INDENT]Here's a recap on the instructions above:

[LIST]
[*][SIZE=-1][FONT=Times New Roman][COLOR=Red][SIZE=2]"You  should clear previous drive  first after you install this driver  source.[/SIZE][/COLOR][/FONT][COLOR=Red]
[/COLOR]  [FONT=Times New Roman][COLOR=Red][SIZE=2]The previous  driver will be  stored within  /lib/modules/2.6.XXX/kernel/driver/staging.[/SIZE][/COLOR][/FONT][COLOR=Red]
[/COLOR]  [FONT=Times New Roman][COLOR=Red][SIZE=2]Please remove  "r8192se_pci.ko" file.[/SIZE][/COLOR][/FONT][COLOR=Red]
[/COLOR]  [FONT=Times New Roman][COLOR=Red][SIZE=2]You could  execute find-name "r8192se_pci.ko" in /lib/modules/2.6.XXX to check it’s  clear properly."[/SIZE][/COLOR][/FONT][/SIZE]
[LIST]
[*][SIZE=-1][FONT=Times New Roman][COLOR=Red][SIZE=2][COLOR=Black]How do I perform this action?  
As you can see above in [COLOR=DarkOrange]Orange[/COLOR] and [COLOR=DarkGreen]Green[COLOR=Black] (also see attached screen shots), I've tried to find this find this file and remove it to no avail.  [COLOR=DarkOrange]I can find it using **PLACES > Search for files...**, but I can't delete it[COLOR=Black].[/COLOR][/COLOR]  [COLOR=DarkGreen]I also tried to find the file in the Terminal, but I don't think I really understood how to do that[/COLOR].[/COLOR][/COLOR][/COLOR]
[/SIZE][/COLOR][/FONT][/SIZE]
[/LIST]
 
[/LIST]
[SIZE=-1][FONT=Times New Roman][COLOR=Red][SIZE=2][COLOR=Black][COLOR=DarkGreen][COLOR=Black]Thank you for taking the time to read this and I really appreciate any help you can provide us

Sincerely,
Bob Marly:guitar:

P.S.  I attempted to post the [/COLOR][/COLOR][/COLOR][/SIZE][/COLOR][/FONT][/SIZE]**[SIZE=-1][FONT=Times New Roman][SIZE=2][COLOR=black]RTL8191SE [/COLOR][/SIZE][/FONT][/SIZE]**[SIZE=-1][FONT=Times New Roman][SIZE=2][COLOR=black]driver file here, but it was to large and the forum wouldn't accept it. this is the error message I received:

[/COLOR][/SIZE][/FONT][/SIZE][INDENT]**rtl8192se_linux_2.6.0017.0525.2010.tar.gz**:
		Your file of 1.89 MB bytes exceeds the forum's limit of 976.6 KB for  this filetype.  	
[/INDENT][SIZE=-1][FONT=Times New Roman][SIZE=2][COLOR=black]If you know a way around this please let me know and I'll post it ASAP for the community.  Thanks.[/COLOR][/SIZE][/FONT][/SIZE]
[SIZE=-1][FONT=Times New Roman][SIZE=2][COLOR=black] [/COLOR][/SIZE][/FONT][/SIZE]

---

### Post by AlexZaim on 2010-07-05
to find:
locate <the_file_name>

To copy a selected text in terminal:
ctrl+insert
To paste in terminal
shift + insert

To remove:
sudo rm /path.to/file.ko
<insert password>

---

### Post by u2rcrazy on 2010-07-12
AlexZaim,

Thanks for your reply.  I just used your directions and they worked most of the way.  The only thing that didn't  work was the remove or rm command.   I received the following reply when typing the remove command:  [FONT=Courier New][COLOR=Red]rm: cannot remove `/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/r8192se_pci.ko': No such file or directory[/COLOR][/FONT].   This is the same message that I received when I tried to delete this file using the Ubuntu GUI.  I have included a screen shot of the terminal that shows everything starting with the "locate" command through this rm command a it's message.
[INDENT][ATTACH]163182[/ATTACH][/INDENT]Thanks,
Bob :)   :P

---

