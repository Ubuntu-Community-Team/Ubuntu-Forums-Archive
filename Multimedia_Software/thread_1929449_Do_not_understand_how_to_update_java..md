---
title: "Do not understand how to update java."
date: 2012-02-22
forum: Multimedia Software
---

### Post by jrc7z on 2012-02-22
[SIZE=1]Am trying to update my Java from a fresh install of ubuntu 11.10, but on reading the how to, there are some phrases that stump the heck out of me.  I am new to linux, obviously.  These are the directions I'm following to remove Java.    I am lost at what file system - opt is supposed to mean/do.  I do not understand.  Is it a statement I should understand?  Is it a command?  Should I be waiting for it to appear? 

  	 	 	 	[/SIZE]   	 	 	 	 	 	 	 	   [SIZE=1][COLOR=#000000]"Do you wish to remove JRE again? It's very easy, to remove a manually installed JRE. As follows:

Close Firefox (otherwise the java plugin will be in use).

Now open file manager Nautilus with root rights, using the following terminal command.

Click on the grey Ubuntu logo (Dash home). Query: [/COLOR][/SIZE][SIZE=1][COLOR=#0000ff]terminal[/COLOR][/SIZE][SIZE=1][COLOR=#000000]. Click on Terminal.[/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#000000]
Type (copy/paste):[/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#0000ff]gksudo nautilus[/COLOR][/SIZE][SIZE=1][COLOR=#000000]

Press Enter.

File system - opt

Click on the folder [/COLOR][/SIZE][SIZE=1][COLOR=#0000ff]java[/COLOR][/SIZE][SIZE=1][COLOR=#000000] and delete it.[/COLOR][/SIZE][SIZE=1]

[/SIZE][SIZE=1][COLOR=#000000]Then remove the Java plugin:

Type in the terminal (copy/paste):[/COLOR][/SIZE][SIZE=1]

[/SIZE][SIZE=1][COLOR=#0000ff]rm ~/.mozilla/plugins/libnpjp2.so[/COLOR][/SIZE][SIZE=1]

[/SIZE][SIZE=1]Press Enter."[/SIZE]

---

### Post by surfer on 2012-02-22
as a principle, software should be installed through the ubuntu (debian) package management. be that from the command line or using a graphical interface such as the Software Center or Synaptic or any of the others.

java is in the package repositories and can be installed in the official way.

here is how you can do it from the command line:
[http://bhaveshnande.blogspot.com/2011/10/installing-sun-java-6-on-ubuntu-1110.html](http://bhaveshnande.blogspot.com/2011/10/installing-sun-java-6-on-ubuntu-1110.html)

---

### Post by jrc7z on 2012-02-22
Installed java7 and now my computer runs extremely slowly.  it takes 30 seconds to boot software center, typing does not register instantly and there is a huge lag on loading any program and typing also now produces lag.  in general it lags behind by about ten or fifteen characters against what I type.

---

