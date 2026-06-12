---
title: "Two soundcards, mono sound only..."
date: 2009-04-12
forum: Multimedia Software
---

### Post by spadewarrior on 2009-04-12
Hi. 

I have these two soundcards:

[PHP]**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/PHP]

I got the Delta 44 recently and, as I understand it, each of the 4 outputs are Mono-only, so you need to route the left/right into two separate outs and then use two leads to plug into a convential phono/aux input on a hi-fi. 

I've no idea where I went wrong, but I couldn't get that to work (mono only, just louder when both leads were plugged in to the stereo even after hours of web research and envy24control tweaking) so I decided I would go back to the bog-standard Intel card for listening (in glorious stereo) and just use the Delta for recording.

Now, however, I still only have mono sound, but on the Intel card. I've no idea how I did this, although I did remove pulseaudio recently due to having trouble getting it to work with jack (which I use for Renoise and various softsynths). Jack I have no issues with at all, though I'm still learning how to use it. Please not that I had many, MANY issues with pulseaudio and so reinstalling it is not really an option. I normally just use esound/alsa when listening to music/web browsing and jack when I need to route things together.

So, any solutions as to how to get stereo sound back? Adjusting the soundcard volume levels in alsamixer appears to do nothing at all.

Here's the output from amixer, in case it's of any use.

[PHP]Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Capture Monitor',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Capture Valid',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'ADC' 'SPDIF-In'
  Item0: 'AC-Link'
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'DAC Clock Source',0
  Capabilities: enum
  Items: 'AC-Link' 'SPDIF-In' 'Both'
  Item0: 'AC-Link'
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
[/PHP]

Thanks.

---

### Post by markbuntu on 2009-04-12
I would suspect you did something in your asoundconf file so you should probably look in there first and try to remember what you did.

If you want help with the Delta 44 ask in the Multimedia Production forum. It is a little slow but the people there really know about pro stuff like that and will point you in the right direction.

Despite all your trials and tribulations and everything you have read there is a fairly easy way to get pulseaudio working properly and to get it to live together with jack. I use pulseaudio and jack together fairly often on my Ubuntu Studio. It really makes some things I do a lot simpler.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by spadewarrior on 2009-04-22
Thanks for your reply and sorry for my late reply!

I have removed the Delta and I am concentrating currently on just getting the onboard card to output stereo. I've reinstalled Intrepid and Pulseaudio and jack seem to be playing along nicely, but I've still got only mono sound (I checked in Renoise by trying to hard pan some samples).

I do not think I have ever edited the asoundconf file, but I have posted it here in case it sheds some light on the problem:

[PHP]#!/usr/bin/python

# (C) 2005 Canonical Ltd.
# Author: Martin Pitt <martin.pitt@ubuntu.com>
# License: GNU General Public License, version 2 or any later version
#
# Modified by: Thomas Hood, Daniel T Chen
#
# Get and set configuration parameters in ~/.asoundrc.asoundconf.

import sys, re, os.path

our_conf_file = os.path.expanduser('~/.asoundrc.asoundconf')
asoundrc_file = os.path.expanduser('~/.asoundrc')
predefs_file = '/usr/share/alsa/alsa.conf'

setting_re_template = '!?\s*%s\s*(?:=|\s)\s*([^;,]+)[;,]?$'

our_conf_header = '''# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
'''

asoundrc_header = '''# ALSA library configuration file
'''

inclusion_comment = '''# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)'''

usage = '''Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
asoundconf set-oss PARAMETER
asoundconf unset-oss
'''


needs_default_card = '''You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.
'''


needs_oss_dev = '''You have omitted a necessary parameter.  Please specify an OSS device (e.g., /dev/dsp).
'''


superuser_warn = '''Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.
'''


def get_default_predefs():
    try:
	if not os.path.exists(predefs_file):
	    return
	predefs_file_entire = open(predefs_file).readlines()
	r = re.compile('^defaults')
	## Between these hashes, add additional unique regexps that
	## must exist at the end of the user's custom asoundrc.
	s = re.compile('^defaults.namehint')
	##
	predefs_list = []
	must_append_predefs_list = []
	for i in predefs_file_entire:
	    if r.match(i) and not s.match(i):
		predefs_list.append(str(i).strip())
	    elif s.match(i):
		must_append_predefs_list.append(str(i).strip())
	for i in must_append_predefs_list:
	    predefs_list.append(str(i).strip())
	return predefs_list
    except IOError:
	pass


def ensure_our_conf_exists():
    '''If it does not exist then generate a default configuration
    file with no settings.

    Return: True on success, False if the file could not be created.
    '''

    if os.path.exists(our_conf_file):
        return True

    try:
        open(our_conf_file, 'w').write(our_conf_header)
        return True
    except IOError:
        print >> sys.stderr, 'Error: could not create', our_conf_file
        return False


def ensure_asound_rc_exists():
    '''Generate a default user configuration file with only the
    inclusion line.

    Return: True on success, False if the file could not be created.
    '''

    if os.path.exists(asoundrc_file):
        return True

    try:
        open(asoundrc_file, 'w').write('%s\n%s\n<%s>\n\n' % (asoundrc_header, inclusion_comment, our_conf_file))
        return True
    except IOError:
        print >> sys.stderr, 'Error: could not create', asoundrc_file
        return False


def sds_transition():
    '''Replace the magic comments added to the user configuration file
    by the obsolete set-default-soundcard program with the standard
    inclusion statement for our configuration file.
    '''

    if not os.path.exists(asoundrc_file):
        return

    lines = open(asoundrc_file).readlines()

    start_marker_re = re.compile('### BEGIN set-default-soundcard')
    end_marker_re = re.compile('### END set-default-soundcard')

    userconf_lines = []
    our_conf_lines = []

    # read up to start comment
    lineno = 0
    found = 0
    for l in lines:
        lineno = lineno+1
        if start_marker_re.match(l):
            found = 1
            break
        userconf_lines.append(l)

    if found:
        # replace magic comment section with include
        userconf_lines.append('%s\n<%s>\n\n' % (inclusion_comment, our_conf_file))
    else:
        # no magic comment
        return

    # read magic comment section until end marker and add it to asoundconf
    found = 0
    for l in lines[lineno:]:
        lineno = lineno+1
        if end_marker_re.match(l):
            found = 1
            break
        if not l.startswith('#'):
            our_conf_lines.append(l)

    if not found:
        # no complete magic comment
        return

    # add the rest to user conf
    userconf_lines = userconf_lines + lines[lineno:]

    # write our configuration file
    if not ensure_our_conf_exists():
        return
    try:
        open(our_conf_file, 'a').writelines(our_conf_lines)
    except IOError:
        return # panic out

    # write user configuration file
    try:
        open(asoundrc_file, 'w').writelines(userconf_lines)
    except IOError:
        pass


def is_active():
    '''Check that the user configuration file is either absent, or,
    if present, that it includifies the asoundconf configuration file;
    in those cases asoundconf can be used to change the user's ALSA
    library configuration.

    Also transition from the legacy set-default-soundcard program.

    Return True if the above condition is met, False if not.
    '''

    if not os.path.exists(asoundrc_file):
        return True

    sds_transition()

    # check whether or not the file has the inclusion line
    include_re = re.compile('\s*<\s*%s\s*>' % our_conf_file)
    for l in open(asoundrc_file):
        if include_re.match(l):
            return True

    return False

def get(prmtr):
    '''Print the value of the given parameter on stdout

    Also transition from the legacy set-default-soundcard program.

    Return True on success, and False if the value is not set.
    '''

    sds_transition()

    if not os.path.exists(our_conf_file):
        return False

    setting_re = re.compile(setting_re_template % prmtr)

    try:
        for line in open(our_conf_file):
            m = setting_re.match(line)
            if m:
                print m.group(1).strip()
                return True
        return False
    except IOError:
        return False

def list():
	'''Get card names from /proc/asound/cards'''

	cardspath = '/proc/asound/cards'
	if not os.path.exists(cardspath):
		return False
	procfile = open(cardspath, 'rb')
	cardline = re.compile('^\s*\d+\s*\[')
	card_lines = []
	lines = procfile.readlines()
	for l in lines:
		if cardline.match(l):
			card_lines.append(re.sub(r'^\s*\d+\s*\[(\w+)\s*\].+','\\1',l))
	print "Names of available sound cards:"
	for cardname in card_lines:
		print cardname.strip()
	return True

def delete(prmtr):
    '''Delete the given parameter.

    Also transition from the legacy set-default-soundcard program.

    Return True on success, and False on an error.
    '''

    sds_transition()

    if not os.path.exists(our_conf_file):
        return False

    setting_re = re.compile(setting_re_template % prmtr)
    lines = []
    try:
        lines = open(our_conf_file).readlines()
    except IOError:
        return False

    found = 0
    for i in xrange(len(lines)):
        if setting_re.match(lines[i]):
            del lines[i]
            found = 1
            break

    if found:
        # write back file
        try:
            f = open(our_conf_file, 'w')
        except IOError:
            return False
        f.writelines(lines)

    return True


def set(prmtr, value):
    '''Set the given parameter to the given value

    Also transition from the legacy set-default-soundcard program.

    Return True on success, and False on an error.
    '''

    sds_transition()

    setting_re = re.compile(setting_re_template % prmtr)
    lines = []

    ensure_asound_rc_exists()
    # N.B. We continue even if asoundrc could not be created
    # and we do NOT ensure that our configuration is "active"

    if not ensure_our_conf_exists():
        return False

    try:
        lines = open(our_conf_file).readlines()
    except IOError:
        return False

    newsetting = '%s %s\n' % (prmtr, value)

    # if setting is already present, change it
    found = 0
    for i in xrange(len(lines)):
        if setting_re.match(lines[i]):
            lines[i] = newsetting
            found = 1
            break

    if not found:
        lines.append(newsetting)

    # write back file
    try:
        f = open(our_conf_file, 'w')
    except IOError:
        return False
    f.writelines(lines)
    return True

def set_default_card(card):
	clist = get_default_predefs()
	sep = re.compile('\s+')
	r = re.compile('^defaults.pcm.card')
	s = re.compile('^defaults.ctl.card')
	## !defaults.pcm.card and defaults.ctl.card should lead
	## the user's custom asoundrc.
	if set('!defaults.pcm.card', card) and \
	   set('defaults.ctl.card', card):
	    for i in clist:
		(j, k) = sep.split(i)
		if not r.match(j) and not s.match(j):
		    if not set(j, k):
			return False
	    return True
	else:
	    return False

def reset_default_card():
	clist = get_default_predefs()
	sep = re.compile('\s+')
	for i in clist:
	    (j, k) = sep.split(i)
	    if not delete(j):
		return False
	return True

def delete_pcm_default():
	return delete('pcm.!default')

def delete_ctl_default():
	return delete('ctl.!default')

def set_pulseaudio():
    return set('pcm.!default', '{ type pulse }') and \
	set('ctl.!default', '{ type pulse }')

def unset_pulseaudio():
    return delete_pcm_default() and \
	delete_ctl_default()

def set_oss(device):
    endbrace = ' }'
    return set('pcm.!default { type oss  device', device + endbrace)

def unset_oss():
    return delete_pcm_default()

def exit_code(result):
    '''Exit program with code 0 if result is True, otherwise exit with code
    1.
    '''

    if result:
        sys.exit(0)
    else:
        sys.exit(1)


##
## main
##

if os.geteuid() == 0:
    print superuser_warn

if len(sys.argv) < 2 or sys.argv[1] == '--help' or sys.argv[1] == '-h':
    print usage
    sys.exit(0)

if sys.argv[1] == 'is-active':
    exit_code(is_active())

if sys.argv[1] == 'get':
    if len(sys.argv) != 3:
        print usage
        sys.exit(1)
    exit_code(get(sys.argv[2]))

if sys.argv[1] == 'delete':
    if len(sys.argv) != 3:
        print usage
        sys.exit(1)
    exit_code(delete(sys.argv[2]))

if sys.argv[1] == 'set':
    if len(sys.argv) != 4:
        print usage
        sys.exit(1)
    exit_code(set(sys.argv[2], sys.argv[3]))

if sys.argv[1] == 'list':
	exit_code(list())

if sys.argv[1] == 'set-default-card':
    if len(sys.argv) != 3:
	print needs_default_card
	sys.exit(1)
    exit_code(set_default_card(sys.argv[2]))

if sys.argv[1] == 'reset-default-card':
	exit_code(reset_default_card())

if sys.argv[1] == 'set-pulseaudio':
	exit_code(set_pulseaudio())

if sys.argv[1] == 'unset-pulseaudio':
	exit_code(unset_pulseaudio())

if sys.argv[1] == 'set-oss':
    if len(sys.argv) != 3:
	print needs_oss_dev
	sys.exit(1)
    exit_code(set_oss(sys.argv[2]))

if sys.argv[1] == 'unset-oss':
	exit_code(unset_oss())

print usage
sys.exit(1)
[/PHP]

---

### Post by markbuntu on 2009-04-22
Did you try reinstalling alsa. That usually fixes screwy problems like that. It is also a good idea to do it when changing or adding/removing sound cards so the autodetect can do its thing properly. 


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

You might want to out the Delta44 back in and then reinstall alsa. It should be working OOB. Try asking about that in the Multimedia Production forum. It can be a little slow but the people there know a lot about the m-audio and other pro sound stuff.

---

### Post by spadewarrior on 2009-04-22
Thanks for the reply, I'll give that a go.

---

