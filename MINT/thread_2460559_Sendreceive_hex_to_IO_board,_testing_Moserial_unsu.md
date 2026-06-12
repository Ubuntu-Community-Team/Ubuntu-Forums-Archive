---
title: "Send/receive hex to I/O board, testing Moserial unsuccessful.  Realterm for linux?"
date: 2021-04-13
forum: MINT
---

### Post by edward210 on 2021-04-13
I'm trying to do a basic communication test of an I/O board (on Linux Mint) that uses a 9 byte hex string, before I begin writing code. You send a read hex string to the board, it responds with a reply hex string.
Pretty simple, it works fine using Realterm on Windows, but I'm struggling to get a response using Moserial on Linux, or picoterm.  Moserial does work properly somewhat as I have tested it with a loopback plug and ASCII. 


Moserial doesn't have the granular settings found in Realterm, the basic settings look correct, but I'm getting no reply from the device using Moserial, when sending a hex string like this (0x00 0x5A 0x58 0z00 0x07 0x00 0x00 0x00 0xB9), or I get an "Invalid Input" dialog from moserial.

I have also tried in moserial:
Outgoing line: 0000 005A 0058 0000 0007 0000 0000 0000 00B9 [Send] [HEX] [No end]
Produced an 'Invalid Input!' dialog box.
---
Outgoing line: 000 05A 058 000 007 000 000 000 0B9 [Send] [HEX] [No end]
Produced an 'Invalid Input!' dialog box.
---
Outgoing line: 00 5A 58 00 07 00 00 00 B9 [Send] [HEX] [No end]
Produced an 'Invalid Input!' dialog box.

This example of Realterm displays sent string in green with the response string in yellow.


[IMG]http://www.buy-fla.com/realterm_ok2.png[/IMG]


Any advice or suggestions of a better serial app would be appreciated.


I'm hoping there is a better software product for this in Linux.

---

### Post by howefield on 2021-04-13
Thread moved to the "*MINT*" forum

---

### Post by edward210 on 2021-04-13
[COLOR=#000000][FONT=Verdana]Solved!![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The hex string (0x00 0x5A 0x58 0z00 0x07 0x00 0x00 0x00 0xB9) in Moserial must be sent:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]005A580007000000B9 [Send] [HEX] [No end][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]It is then displayed as:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00000000 00 5A 58 00 07 00 00 00 B9 and gets the correct reply from the I/O board.[/FONT][/COLOR]

---

