---
title: "USB-UIRT DCH3416 IR Blaster Pronto Codes"
date: 2009-07-12
forum: Multimedia Software
---

### Post by brw02005 on 2009-07-12
I have a USB-UIRT working but it is unable to use irrecord to create a descent conf file for my DCH3416.  If anyone has a conf file I'm off to the races or can convert pronto codes from a windows program I have let me know.  I tried using pronto2lirc script I found in a forum but it produced a raw command that would lock up my usb-uirt. I plugged in a lird conf for my xbox and confirmed that it does in fact work.  If anyone has a link to an IR Blaster known to work for a DCH3416 I would also consider it.

Hardware.conf

# /etc/lirc/hardware.conf
#

#Chosen IR Transmitter
TRANSMITTER="USB-UIRT2 : Motorola Cable box"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="usb_uirt_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
#LIRCD_ARGS="-d /dev/ttyUSB0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
#LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
#DRIVER="uirt2_raw"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE=""
#MODULES=""

# Default configuration files for your hardware if any
#LIRCD_CONF=""
#LIRCMD_CONF=""

Failed attempt at using pronto codes to create a lircd

begin remote
	name	Pronto
	flags	RAW_CODES
	eps	30
	aeps	100
	gap	87595
		begin raw_codes

			name POWER
				8937 4481 495 2241 495 4481 
				495 2241 495 4481 495 2241 
				495 2241 495 2241 495 2241 
				495 2241 495 2241 495 2241 
				495 2241 495 2241 495 4481 
				495 4481 495 2241 495 32568 
				8937 2267 495 

			name 1
				8963 4481 495 4507 495 2267 
				495 2267 495 2267 495 2267 
				495 2267 495 2267 495 2267 
				495 2267 495 2267 495 2267 
				495 2267 495 4507 495 4507 
				495 4507 495 4507 495 30406 
				8963 2267 495 
		end raw_codes
end remote

original pronto codes

POWER: 0000 006C 0012 0002 0157 00AC 0013 0056 0013 00AC 0013 0056 0013 00AC 0013 0056 0013 0056 0013 0056 0013 0056 0013 0056 0013 0056 0013 0056 0013 0056 0013 0056 0013 00AC 0013 00AC 0013 0056 0013 04E2 0157 0057 0013 0D1E

1: 0000 006C 0012 0002 0158 00AC 0013 00AD 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 0057 0013 00AD 0013 00AD 0013 00AD 0013 00AD 0013 048F 0158 0057 0013 0D22

bad conf file from irrecord


# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(usb_uirt_raw) on Sun Jul 12 04:38:10 2009
#
# contributed by 
#
# brand:                       blah.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name   blah.conf
  flags RAW_CODES|CONST_LENGTH
  eps            30
  aeps          100

  ptrail          0
  repeat     0     0
  gap          97303

      begin raw_codes

          name 1
             8850    2200     550

          name 2
             8550    2500     200

          name 3
             8800    2150     500
          name 4
             8850    2200     550

          name 5
             8850    2200     550

          name 6
             8750    2350     400

          name 7
             8850    2250     500

          name 8
             8800    2300     450

          name 9
             8800    2300     400

          name 0
             8850    2200     500

          name POWER
             8800    2150     500
      end raw_codes

end remote

---

