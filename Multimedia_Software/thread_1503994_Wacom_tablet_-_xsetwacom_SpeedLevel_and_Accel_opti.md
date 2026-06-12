---
title: "Wacom tablet - xsetwacom SpeedLevel and Accel options gone from Lucid"
date: 2010-06-07
forum: Multimedia Software
---

### Post by ola on 2010-06-07
Hi,

I started a thread when testing Lucid [http://ubuntuforums.org/showthread.php?t=1435225](http://ubuntuforums.org/showthread.php?t=1435225) This thread takes of where it ended.

In Karmic I could adjust the SpeedLevel and Accel settings for my Wacom tablet via

```

$xsetwacom set "Wacom Graphire4 6x8" SpeedLevel 5
$xsetwacom set "Wacom Graphire4 6x8" Accel 7

```

In Lucid that just gives:
```

$ xsetwacom set "Wacom Graphire4 6x8" SpeedLevel 5 && xsetwacom set "Wacom Graphire4 6x8" Accel 7
Unknown parameter name 'SpeedLevel'.
Unknown parameter name 'Accel'.

```

You can probably use xinput to get the similar setup and I'm just started out playing with the following settings:

```

xinput set-prop "Wacom Graphire4 6x8" "Device Accel Constant Deceleration" 1.2
xinput set-prop "Wacom Graphire4 6x8" "Device Accel Adaptive Deceleration" 1.0
xinput set-prop "Wacom Graphire4 6x8" "Device Accel Velocity Scaling" 250.0

```

I'm not sure what they all mean yet but I'll eventually figure it out.

I would like to find the matching SpeedLevels 5 and Accel 7 options using xinput. Anyone got any experience from setting it up?

---

### Post by Favux on 2010-06-07
Hi ola,

They rewrote the xsetwacom commands for xf86-input-wacom.

They also just added a 'man xsetwacom' in addition to the 'man wacom'.  Here it is:
> .\" shorthand for double quote that works everywhere.
.ds q \N'34'
.TH xsetwacom __appmansuffix__ __vendorversion__
.SH NAME
.LP
xsetwacom \- commandline utility to query and modify __drivername__ driver settings.
.SH "SYNOPSIS"
.LP
xsetwacom [options] command [device_name] [parameter] [value]

.SH "DESCRIPTION"
.LP
This program queries or changes properties on the devices loaded by the
__drivername__ driver. The modification of properties happens at runtime
and is not persistent through X server restarts.
.SH "GENERAL OPTIONS"
.TP
\fB-d, --display\fR display_name
Connect to the X server specified in display_name; see X(__miscmansuffix__).
.TP
\fB-h, --help\fR
Prints a short help.
.TP
\fB-v, --verbose\fR
Enable verbose output, useful for debugging.
.TP
\fB-V, --version\fR
Display version number and exit.

.SH "COMMANDS"
.LP
Allowed commands are
.B list,
.B get,
and
.B set.
The command may be specified with our without one or two preceding
dashes, i.e.
.B --list
is equivalent to
.B -list
and
.B list.

.SS "LIST COMMANDS"
.TP
\fBlist\fR dev
List known devices. Only input devices managed by the __drivername__
driver are listed.
.TP
\fBlist\fR param
List known parameters. List all parameters suitable for the
.B get
or the
.B set
command. Note that not all parameters are available on all device types.
.TP
\fBlist\fR mods
.B Not implemented!
List the available list of modifiers to be used when setting key or button
actions.

.SS "GET COMMANDS"
.TP
\fBget\fR device_name parameter
Get the current settings for the parameter on the given device. Note that
not all parameters are available on all device types. The special parameter
name "all" may be provided to display all current settings on the device.
.TP
By default, options are printed on the commandline in the respective format. The output format may be altered with one of the following options:
.TP
\fB-s, --shell\fR
Display the output in shell format, i.e. as shell commands to xsetwacom to
reproduce the same parameter.
.TP
\fB-x, --xconf\fR
Display the output in xorg.conf format, i.e. as option lines that may be
added to the InputDevice section in the xorg.conf.

.SS "SET COMMANDS"
.TP
\fBset\fR device_name parameter value
Set the parameter value on the given device to the value provided. Note that
not all parameters are writable, some are read-only and result in an error
when trying to be modified.

.SH "AUTHORS"
Peter Hutterer <peter.hutterer@redhat.com>

.SH "SEE ALSO"
__xservername__(__appmansuffix__), wacom(__drivermansuffix__),
xorg.conf(__filemansuffix__),
X(__miscmansuffix__)

---

### Post by ola on 2010-06-07
Thanks a lot, I don't think it helped though (I couldn't find any new info there).

---

