---
title: "applescript: What is it?"
date: 2007-03-24
forum: Mac OSX
---

### Post by TheRingmaster on 2007-03-24
I was reading some of the articles about the new features of tiger and I came across applescript. It looks very readable and easy (maybe too easy). I was wondering if anyone can elaborate on this subject a little more.

---

### Post by 23meg on 2007-03-24
It's a scripting language that focuses on readability. As well as for simple daily tasks, it can be used in conjunction with Cocoa to make complex GUI applications.

 This may be a good start:

[http://en.wikipedia.org/wiki/Applescript](http://en.wikipedia.org/wiki/Applescript)

---

### Post by 3rdalbum on 2007-03-25
Applescript certainly isn't a new feature of Tiger, it's beeen around since System 7 :-)

Whether it's easy or not depends on the kind of person you are. When I started multimedia programming, I preferred the Hypertalk/Applescript/Lingo style of verbose programming. Once I got more advanced, I realised that the verbose kind of programming made it difficult to string together multiple statements, and also made it slower for me to read back afterwards.

One thing I *did* like was being able to run Applescript commands from within Hypercard, but at the time not too many programs actually had useful Applescript commands. The situation with that probably hasn't changed much, as recently many new programs for Mac are just ports of Windows apps.

I do highly doubt the usefulness of Applescript in writing "complex GUI applications". I do remember that Applescript was slower than Python; probably still is.

My advice is to use Pythoncard - that way you get the flexibility of the language and "batteries included", but you can also build GUI programs very easily.

---

### Post by Alfa989 on 2007-03-25
> **3rdalbum said:**
> 
I do highly doubt the usefulness of Applescript in writing "complex GUI applications". I do remember that Applescript was slower than Python; probably still is.

I haven't tried Python, but recently I made a Cocoa app where the main actions used applescript to get achieve the desired results: It was quick and easy... :)

---

### Post by stalefries on 2007-03-26
I've toyed around with AppleScript a bit; its main selling points are that it is verey easy to understand what it does, even if you do not know the language, and that a lot of applications have hooks for it.

---

### Post by rccharles on 2007-03-30
> **TheRingmaster said:**
> . It looks very readable and easy (maybe too easy). I was wondering if anyone can elaborate on this subject a little more.
```

(* Decide whether to start the terminal or switch to a existing terminal. *)

-- Write a message into the event log.
log "  --- Starting on " & ((current date) as string) & " --- "

set myUser to do shell script "echo $USER"

try
	set myApps to do shell script "/bin/ps wwuxU " & myUser
on error
	display dialog "an error has occurred."
end try

if myApps contains "Terminal.app" then
	tell application "Finder"
		open application file "Terminal.app" of folder "Utilities" of folder "Applications" of startup disk
		
	end tell
else
	tell application "Finder"
		open document file "Terminal.term" of folder "Applescript files" of folder "Applications" of startup disk
	end tell
end if

```

I find the syntax and keywords hard to remember.

Robert

---

### Post by 3rdalbum on 2007-03-30
The equivilant of that in Python would be something like:

```

#Decide whether to start the terminal or switch to a existing terminal.
import commands

myUser = commands.getoutput("echo $USER")

try:
	myApps = commands.getoutput("/bin/ps wwuxU " + myUser)
except:
	commands.getoutput("zenity --error --text=\"an error has occurred.\"")


if (myApps.find("Terminal.app") != -1):
	commands.getoutput("Terminal.app")
else:
	commands.getoutput("/Applications/Applescript\ files/Terminal.term")

```

Of course,  the Python example was much less verbose, and I actually found it more readable. Applescript does rock for easy interapplication communication.

---

