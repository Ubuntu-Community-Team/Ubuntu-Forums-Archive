---
title: "Python script of 'sudo make me a sandwich' joke by XKCD"
date: 2011-02-05
forum: Multimedia Software
---

### Post by clockworkpc on 2011-02-05
Hi everyone,

I've written a script in Python that plays out the joke by XKCD about sudo, and I'd much appreciate it anyone could help me write it better.

To make full use of it you will need the following:

[LIST=1]
[*]sudo apt-get install espeak*
[*]Install the latest version of xcowsay from the website, which involves compiling it unfortunately (I have a [bash script]("http://ubuntuforums.org/showthread.php?t=1682417") that will take care of it for you though)
[*]A picture of a sandwich called sandwich.jpg
[*]EITHER have the JPG located at /media/DATA/Pictures/sandwich.jpg OR change line 37
[*]Python installed, obviously, but if you use Linux that should be installed out of the box
[/LIST]

Limitations:

[LIST=1]
[*]Unless you spell it exactly as it reads in the text, i.e. all lower case, no punctuation, it will read it as not being equal to either "make me a sandwich" or "sudo make me a sandwich".
[*]You have to manually close the JPG of the sandwich in order to allow the script to finish.
[/LIST]

```
[COLOR="Blue"][FONT="Verdana"]#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
#       untitled.py
#       
#       Copyright 2011 Clockwork PC
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.
#       

import os
import time

sudo_command = "sudo make me a sandwich"
running = True

while running:
	request = (raw_input('What do you want? '))

	if request == "sudo make me a sandwich":
		print "OK"
		os.system("gnome-terminal -x xcowsay --time=1 --cow-size=large --monitor=0 'OK... Here you go'")
		os.system("espeak 'OK... Here you go'")
		os.system("gpicview /media/DATA/Pictures/sandwich.jpg")
		time.sleep(2)
		"""How do I get it to kill gpicview?"""
		os.system("gnome-terminal -x xcowsay --cow-size=large --monitor=0 'That is all you will get from me.  Cheerio!'")
		os.system("espeak 'That is all you will get from me. Cheerio!'")
		running = False

	if request != "sudo make me a sandwich":
		if request == "make me a sandwich":
			print "Make it yourself"
			os.system("gnome-terminal -x xcowsay --time=1 --cow-size=large --monitor=0 'Make it yourself'")
			os.system("espeak 'Make it yourself'")
		else:
			print "Mate, bugger off"
			os.system("gnome-terminal -x xcowsay --time=1 --cow-size=large --monitor=0 'Mate, bugger off'")
			os.system("espeak 'Mate, bugger off'")



"""if request == "sudo make me a sandwich":
	print "OK"
	os.system("espeak OK")
elif request == "make me a sandwich":
	print "Make it yourself"
	os.system("espeak 'Make it yourself'")
else:
	print "**** off"
	os.system("espeak 'Mate, bugger off'")"""[/FONT][/COLOR]
```

---

