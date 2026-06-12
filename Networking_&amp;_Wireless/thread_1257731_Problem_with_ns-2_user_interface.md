---
title: "Problem with ns-2 user interface"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by Rohit_1989 on 2009-09-04
Hi,
I installed ns-2 network simulator and the installation was fine, I've edited the .bashrc file and path variables are set.
ns runs fine on the command line but when I run the user interface file nstk the following error comes up.
```
Application initialization failed: Can't find a usable tk.tcl in the following directories: 
    /home/rohit/ns-allinone-2.33/lib/tcl8.4/tk8.4 /home/rohit/ns-allinone-2.33/lib/tk8.4 /home/rohit/lib/tk8.4 /home/rohit/ns-allinone-2.33/library /home/rohit/library /home/rohit/tk8.4.18/library /home/tk8.4.18/library

/home/rohit/ns-allinone-2.33/lib/tk8.4/tk.tcl: no event type or button # or keysym
no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
        %W yview scroll [expr {- (%D / 120) * 4}] units
    }"
    invoked from within
"if {[tk windowingsystem] eq "classic" || [tk windowingsystem] eq "aqua"} {
    bind Listbox <MouseWheel> {
        %W yview scroll [expr {- (%D)}] uni..."
    (file "/home/rohit/ns-allinone-2.33/lib/tk8.4/listbox.tcl" line 181)
    invoked from within
"source /home/rohit/ns-allinone-2.33/lib/tk8.4/listbox.tcl"
    (in namespace eval "::" script line 1)
    invoked from within
"namespace eval :: [list source [file join $::tk_library $file.tcl]]"
    (procedure "SourceLibFile" line 2)
    invoked from within
"SourceLibFile listbox"
    (in namespace eval "::tk" script line 4)
    invoked from within
"namespace eval ::tk {
	SourceLibFile button
	SourceLibFile entry
	SourceLibFile listbox
	SourceLibFile menu
	SourceLibFile panedwindow
	SourceLibFile ..."
    invoked from within
"if {$::tk_library ne ""} {
    if {$tcl_platform(platform) eq "macintosh"} {
	proc ::tk::SourceLibFile {file} {
	    if {[catch {
		namespace eval :: ..."
    (file "/home/rohit/ns-allinone-2.33/lib/tk8.4/tk.tcl" line 407)
    invoked from within
"source /home/rohit/ns-allinone-2.33/lib/tk8.4/tk.tcl"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list source $file]"


This probably means that tk wasn't installed properly.
```

I've installed tk(version 8.4) in my system and tcl aswell.

Please help me out!

---

