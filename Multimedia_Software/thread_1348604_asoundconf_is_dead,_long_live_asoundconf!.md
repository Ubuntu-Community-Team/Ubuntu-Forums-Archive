---
title: "asoundconf is dead, long live asoundconf!"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Ghost|BTFH on 2009-12-07
I wanted to bring up yet another ugly little hack that's required in Karmic Koala, all thanks to the failures of the PulseAudio brigade and their tomfoolery.

Now this is for those who do not believe in having PulseAudio in their cute cuddly Koala.  If you have Karmic Koala, you're running ALSA and have multiple sound cards, this post is for you.

Alsa-utils no longer has asoundconf which, if you don't know, is like a car not having a transmission.

What it does:  Allows the user to switch between two sound cards (for example, on-board sound and a USB headset)

When you need it:  Only for certain situations where it is necessary to use a secondary sound card for specific things (Such as running a voice program in Virtualbox on a USB headset - which will not work with PulseAudio and some hardware, no matter how hard you try).

What you have to do:  Cheap hacks.  Let me repeat - This is a crappy little hack that should not have to be done.  

Step 1: Go to [http://packages.ubuntu.com/jaunty/alsa-utils](http://packages.ubuntu.com/jaunty/alsa-utils) and download the alsa-utils for your version of ubuntu (i386 or amd64).

Step 2: Open a terminal and cd to the download directory and run:

sudo dpkg -i alsa-utils_1.0.18-1ubuntu11_amd64.deb

Step 3: Now, after this mess, cd to /usr/bin and use this command:

sudo cp asoundconf /usr/

Which will copy (cp) asoundconf (the file you want) to the directory /usr/

Step 4: Run:

sudo apt-get install asoundconf-gtk

This will install a very nice simple gtk frontend for the asoundconf file that is no longer in existence in our software...wait what?  Yeah I know, they kept the gtk and removed the actual file the gtk uses.  Go figure.

Step 5: Anyhow, next step is to run your update manager in whatever style you prefer, I just use System -> Administration -> Update manager.

This will destroy all the fine hard work you did to install asoundconf to begin with.  However!  All is not lost...your alsa-utils are now updated.

Step 6:  cd to /usr and type:

cp asoundconf /usr/bin/

You will now have asoundconf in /usr/bin and it will work just fine.

To test this, run asoundconf-gtk and see if it comes up, if it does, everything's fine.  If it doesn't, something went horribly wrong.

If it worked fine, you can now select from the detected sound cards in your system.

Step 6 most likely will have to be repeated for each alsa-utils upgrade done, but hey, it's better than not being able to swap between two or more sound cards without using PulseAudio

For those wondering why this has happened, it's because the person who was maintaining asoundconf is no longer doing so.  Seriously, that's the only reason.  We just need someone who knows what they're doing to maintain it again and we won't have to deal with these inglorious hacks.

Stay loud, talk hard.

Cheers,
Ghost|BTFH

---

### Post by Chris Edgell on 2009-12-09
bump

---

### Post by Tumpster on 2009-12-09
craig@craig-desktop:/usr$ cp asoundconf /usr/bin/
cp: cannot create regular file `/usr/bin/asoundconf': Permission denied
craig@craig-desktop:/usr$ sudo cp asoundconf /usr/bin/
craig@craig-desktop:/usr$ asoundconf-gtk
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

Why is this not working? I removed pulse audio completely and try this with running only ALSA to no success.

---

### Post by Ghost|BTFH on 2009-12-09
> **Tumpster said:**
> craig@craig-desktop:/usr$ cp asoundconf /usr/bin/
cp: cannot create regular file `/usr/bin/asoundconf': Permission denied
craig@craig-desktop:/usr$ sudo cp asoundconf /usr/bin/
craig@craig-desktop:/usr$ asoundconf-gtk
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

Why is this not working? I removed pulse audio completely and try this with running only ALSA to no success.

1) Did you have sound working in ALSA before you did this?

2) Did you give it a reboot after removing pulse and installing ALSA?

3) I'm presuming you did, but did you follow each step including selecting the correct version of your OS?

If yes to all, did you try doing:

asoundconf is-active

in terminal?  It might be something I'd done and hadn't remembered to mention.

I'm hoping we can get to the bottom of this for you.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-10
> **Ghost|BTFH said:**
> 1) Did you have sound working in ALSA before you did this?

2) Did you give it a reboot after removing pulse and installing ALSA?

3) I'm presuming you did, but did you follow each step including selecting the correct version of your OS?

If yes to all, did you try doing:

asoundconf is-active

in terminal?  It might be something I'd done and hadn't remembered to mention.

I'm hoping we can get to the bottom of this for you.

Cheers,
Ghost

I never honestly checked alsa before I removed pulseaudio, I just removed pulseaudio and switched to alsa and have had no troubles with it. I did reboot after almost every major change between going from pulse to alsa and finally I input that asoundconf is-active and nothing came up just bumped to my next line. What could I be doing wrong or can I do?

---

### Post by Ghost|BTFH on 2009-12-11
If I recall correctly, just doing

*asoundconf is active*

should be enough to make asoundconf work.

You should have alsa properly installed, everything switched over to it and asoundconf should work.

You could test it by trying

*asoundconf list*

If you get a list of the sound cards you have in your system - it's working.

Otherwise, we'd have to go back to the start and see what you did to remove pulse/install alsa.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-11
> **Ghost|BTFH said:**
> If I recall correctly, just doing

*asoundconf is active*

should be enough to make asoundconf work.

You should have alsa properly installed, everything switched over to it and asoundconf should work.

You could test it by trying

*asoundconf list*

If you get a list of the sound cards you have in your system - it's working.

Otherwise, we'd have to go back to the start and see what you did to remove pulse/install alsa.

Cheers,
Ghost

I get nothing from Ubuntu when I input that. To remove Pulse I
followed this step by step:
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4)

---

### Post by Ghost|BTFH on 2009-12-11
> **Tumpster said:**
> I get nothing from Ubuntu when I input that. To remove Pulse I
followed this step by step:
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4)

I have no clue what could be wrong.  To remove pulse, I just did the following, as I posted in this link.

[http://ubuntuforums.org/showthread.php?t=1306679&highlight=sound+advice](http://ubuntuforums.org/showthread.php?t=1306679&highlight=sound+advice)

To get asoundconf working, I did exactly as I stated above, nothing else.

It worked perfectly.  I'm honestly stumped as to why you would have any issue at all with it, unless you grabbed say, the amd64 file when you had i386 on your system, or vice versa.

Other than that, it does not make any logical sense that you would have any issues with this.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-13
> **Ghost|BTFH said:**
> I have no clue what could be wrong.  To remove pulse, I just did the following, as I posted in this link.

[http://ubuntuforums.org/showthread.php?t=1306679&highlight=sound+advice](http://ubuntuforums.org/showthread.php?t=1306679&highlight=sound+advice)

To get asoundconf working, I did exactly as I stated above, nothing else.

It worked perfectly.  I'm honestly stumped as to why you would have any issue at all with it, unless you grabbed say, the amd64 file when you had i386 on your system, or vice versa.

Other than that, it does not make any logical sense that you would have any issues with this.

Cheers,
Ghost


Here is the output of both my asound.conf and my asound gtk:

#!/usr/bin/python

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
asoundconf set-alsa
asoundconf unset-alsa
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

def set_alsa():
    return set('pcm.!default', '{ type alsa }') and \
	set('ctl.!default', '{ type alsa }')

def unset_alsa():
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

if sys.argv[1] == 'set-alsa':
	exit_code(set_alsa())

if sys.argv[1] == 'unset-alsa':
	exit_code(unset_alsa())

if sys.argv[1] == 'set-oss':
    if len(sys.argv) != 3:
	print needs_oss_dev
	sys.exit(1)
    exit_code(set_oss(sys.argv[2]))

if sys.argv[1] == 'unset-oss':
	exit_code(unset_oss())

print usage
sys.exit(1)



And my asound gtk:
#!/usr/bin/env python
# asoundconf-gtk - GTK GUI to select the default sound card
#
# (C) 2006 Toby Smithe
# asoundconf parts (C) 2005 Canonical Ltd.
# gourmet parts (C) 2005 Thomas Hinkle (and any other gourmet developers)
# Both the asoundconf and gourmet projects are also licenced under the 
# GPLv2 or any later version in exactly the same way as this project.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

import sys, re, os, pygtk, gtk, string

######################################
#START small block of asoundconf code#
######################################

def getcards():
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
	return card_lines # Snipped here

####################################
#END small block of asoundconf code#
####################################

###################################
#START small block of gourmet code#
###################################

def cb_set_active_text (combobox, text, col=0):
    """Set the active text of combobox to text. We fail
    if the text is not already in the model. Column is the column
    of the model from which text is drawn."""
    model = combobox.get_model()
    n = 0
    for rw in model:
        if rw[col]==text:
            combobox.set_active(n)
            return n
       	n += 1
    return None

#################################
#END small block of gourmet code#
#################################

asoundconf = "/usr/bin/asoundconf"

def die_on_error():
	'''Kill the application if it cannot run'''
	if not os.path.exists("/proc/asound/cards"):
		print "You need at least one ALSA sound card for this to work!"
		sys.exit(-1)
	if os.system(asoundconf + " is-active"):
		print "You need to make sure asoundconf is active!"
		print "By default, asoundconf's configuration file is ~/.asoundrc.asoundconf"
		print "and must be included in ~/.asoundrc. Open this file to make sure it is!"
		sys.exit(-2)

def get(setting):
	'''Get an asoundconf setting'''
	cmd = asoundconf + " get " + setting
	output = os.popen(cmd).readlines()
	return output

def get_default_card():
	'''# Get the default PCM card (but assume this is the default card for everything)
	This is just a very simple wrapper for get(...) as otherwise I'd have to repeat
	a load (well, two lines) of code.'''
	value_raw = get("defaults.pcm.card")
	if not value_raw:
		return 0
	value = string.strip(value_raw[0])
	return value

def set_default_card(card):
	'''Set the default card using asoundconf'''
	call = asoundconf + " set-default-card " + card
	return os.system(call)

def set_pulseaudio():
	call = asoundconf + " set-pulseaudio"
	return os.system(call)

def unset_pulseaudio():
	call = asoundconf + " unset-pulseaudio"
	return os.system(call)
	
class asoundconf_gtk:
	def destroy(self, widget, data=None):
		'''This is a stub function to allow for stuff to be done on close'''
		gtk.main_quit()

	def delete_event(self, widget, event, data=None):
		'''Again, a stub to allow stuff to happen when widgets are deleted'''
		return False

	def choose(self, widget, data=None):
		'''Function to set thde default card on choice'''
		card = widget.get_active_text()
		if card == "PulseAudio":
			set_pulseaudio()
		else:
			unset_pulseaudio()
			set_default_card(card)

	def pulse(self, widget, data=None):
		'''Enables/Disables PulseAudio support'''
		active = widget.get_active()
		if active:
			value = set_pulseaudio()
		else:
			value = unset_pulseaudio()
		return value

	def reset(self, widget, data=None):
		'''Reset the default card to the current default'''
		if self.combo.get_active_text() == "PulseAudio":
			set_pulseaudio()
		else:
			unset_pulseaudio()			
			set_default_card(get_default_card())
	
	def __init__(self):
		# Initiate the window
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Default Sound Card")
		# Create an HBox box
		self.selectionbox = gtk.HBox(False, 0)
		# Create a button
		self.button = gtk.Button("Quit")
		self.button.connect("clicked", self.reset, None)
		self.button.connect_object("clicked", gtk.Widget.destroy, self.window)
		# Create combobox
		self.combo = gtk.combo_box_new_text()
		self.liststore = self.combo.get_model()
		# Add cards to combobox liststore
		cards = getcards()
		if not cards:
			return False
		for card in cards:
			self.combo.append_text(card.strip())
		self.combo.connect("changed", self.choose, None)
		# Create a label
		self.label = gtk.Label("Select default card: ")
		# Add contents to HBox "selectionbox"
		self.selectionbox.pack_start(self.combo, True, True, 0)		
		self.selectionbox.pack_start(self.button, True, True, 0)
		# Create a VBox
		self.vbox = gtk.VBox(False, 0)
		self.window.add(self.vbox)
		self.vbox.pack_start(self.label, True, True, 0)
		self.vbox.pack_start(self.selectionbox, True, True, 0)
		# Create PulseAudio checkbox if ALSA PulseAudio plugin installed
		if os.path.exists("/usr/lib/alsa-lib/libasound_module_pcm_pulse.so") and os.path.exists("/usr/lib/alsa-lib/libasound_module_ctl_pulse.so"):
			#self.pulsecheck = gtk.CheckButton("Use _PulseAudio?")
			self.combo.append_text("PulseAudio")
			try: pcmDefault = get("pcm.!default")[0]
			except: pcmDefault = ""
			if pcmDefault == "{ type pulse }\n":
				#self.pulsecheck.set_active(True)
				cb_set_active_text(self.combo, "PulseAudio")
			else:
				# Select current default 
				cb_set_active_text(self.combo, get_default_card())
			#self.pulsecheck.connect("toggled", self.pulse, None)
			#self.vbox.pack_start(self.pulsecheck, True, True, 0)
		# Connect up window events
		self.window.connect("destroy",self.destroy)
		self.window.connect("delete_event",self.delete_event)
		# Show window and contents
		self.window.show_all()

	def main(self):
		'''Do the stuffs'''
		gtk.main()

if __name__ == "__main__":
	die_on_error()
	aconf = asoundconf_gtk()
	sys.exit(aconf.main())

---

### Post by Ghost|BTFH on 2009-12-13
Okay, asoundconf-gtk isn't going to work until asoundconf works.  Simple as that.

On the asoundconf part, I'm guessing you have not done:

*asoundconf list*

which will tell you what cards you have in there, and then 

*asoundconf set-default-card (one of the selections goes here)*

***Example: asoundconf list gives you SB and USB for your two options, do asoundconf set-default-card SB***

Do that, and it should straighten itself out then.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-13
craig@craig-desktop:~$ asoundconf list
Names of available sound cards:
Live
craig@craig-desktop:~$ asoundconf set-default-card Live
craig@craig-desktop:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-alsa
asoundconf unset-alsa
asoundconf set-oss PARAMETER
asoundconf unset-oss

craig@craig-desktop:~$ asound-gtk
asound-gtk: command not found
craig@craig-desktop:~$ asoundconf-gtk
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
craig@craig-desktop:~$

---

### Post by Ghost|BTFH on 2009-12-13
Well, you almost got through it...
[I]
asoundconf is-active[/I]

Is actually a command you need to type into the terminal, just in case you didn't know this.

Aside from that, it looks like everything's working just fine.  Unless you haven't set asoundconf as active (like the above command does) and you haven't restarted your desktop, I really can't imagine what the issue is.

Also, just to note - your asoundconf did not show any other sound card.  Either you don't have it plugged in at the moment, or there's a serious issue.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-14
> **Ghost|BTFH said:**
> Well, you almost got through it...
[I]
asoundconf is-active[/I]

Is actually a command you need to type into the terminal, just in case you didn't know this.

Aside from that, it looks like everything's working just fine.  Unless you haven't set asoundconf as active (like the above command does) and you haven't restarted your desktop, I really can't imagine what the issue is.

Also, just to note - your asoundconf did not show any other sound card.  Either you don't have it plugged in at the moment, or there's a serious issue.

Cheers,
Ghost

Yeah I turned the onboard back on now. But I input this and got this response:
craig@craig-desktop:~$ asoundconf is-active
  File "/usr/bin/asoundconf", line 53
    needs_oss_dev = '''You have omitted a necessary parameter.  Please specify an OSS device (e.g., /dev/dsp).
                         ^
SyntaxError: invalid syntax
craig@craig-desktop:~$

---

### Post by Ghost|BTFH on 2009-12-14
Do you not have ALSA-OSS?

Make sure you have that installed and give it another go.

---

### Post by Yellow Pasque on 2009-12-14
This will also help you run "Pulse-less": [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by Ghost|BTFH on 2009-12-14
> **Temüjin said:**
> This will also help you run "Pulse-less": [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

I don't think his issue is going pulse-less, I think he just didn't have everything he needed installed when he set up ALSA.

---

### Post by Tumpster on 2009-12-14
craig@craig-desktop:~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-16 pidgin-data linux-headers-2.6.31-16-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
craig@craig-desktop:~$

---

### Post by Ghost|BTFH on 2009-12-14
I'm honestly at a loss Tumpster.

At this point, it's a guessing game...okay, it's asking to set a device for oss...

What if we did...

*asoundconf set-oss Live*

and see if that works?

---

### Post by Tumpster on 2009-12-15
craig@craig-desktop:~$ asounconf-gtk
No command 'asounconf-gtk' found, did you mean:
 Command 'asoundconf-gtk' from package 'asoundconf-gtk' (universe)
asounconf-gtk: command not found
craig@craig-desktop:~$ asoundconf-gtk
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 49, in <module>
    needs_default_card = Live
NameError: name 'Live' is not defined
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

---

### Post by Ghost|BTFH on 2009-12-15
Okay, again...let's do what it says.

*gedit ~/asoundrc.asoundconf*

 Make sure Live is set as the default card.  If you don't have anything written in the file, then for some reason, you don't have things fully set up.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-15
> **Ghost|BTFH said:**
> Okay, again...let's do what it says.

*gedit ~/asoundrc.asoundconf*

 Make sure Live is set as the default card.  If you don't have anything written in the file, then for some reason, you don't have things fully set up.

Cheers,
Ghost

Upon running this command, it opens to a blank document. Should this file exsist? And if so what should be in it?

---

### Post by Ghost|BTFH on 2009-12-15
I believe we may have found your issue then...

Make sure you didn't mistype it, otherwise, this is what is in my *.asoundrc.asoundconf* file:

[B]# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card SB
defaults.ctl.card SB
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off[/B]

I would change the SB to Live and leave the rest as-is.  Then try running asoundconf and see what happens.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-15
craig@craig-desktop:~$ asoundconf
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 49, in <module>
    needs_default_card = Live
NameError: name 'Live' is not defined

---

### Post by Ghost|BTFH on 2009-12-15
Well, it looks like there was something screwed up in the process you went about removing pulseaudio and installing alsa that certain files just were not created like they should have been.

I was hoping it'd be maybe one thing missing or written incorrectly, but it appears that you have a slight mess...

Might I suggest going into your Synaptic Package Manager and making sure you have the following (I'm copying my list of installed programs just to be safe):
[B]
alsa-base
alsamixergui
alsa-oss
alsa-tools
alsa-utils
asoundconf-gtk
gnome-alsamixer
gstreamer0.10-alsa
lib32asound2
libao2
libasound2
libasound2-plugins
liblash2
libopenal1
libpt2.6.4-plugins
linux-sound-base[/B]

I would suggest perhaps highlighting them all and mark them for install or reinstallation if they are already all installed.

Then restart your desktop (or reboot) and see if it works finally.

You will also have to copy asoundconf back into the */usr/bin* of course.

Beyond this, you may need an exorcist for your computer.

Cheers,
Ghost

---

### Post by Tumpster on 2009-12-15
craig@craig-desktop:~$ sudo apt-get install lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32asound2
craig@craig-desktop:~$ 


Reinstalled everything else and will be rebooting shortly.

After reboot:
craig@craig-desktop:~$ sudo cp asoundconf /usr/
[sudo] password for craig: 
Sorry, try again.
[sudo] password for craig: 
cp: cannot stat `asoundconf': No such file or directory
craig@craig-desktop:~$ cd /usr/bin
craig@craig-desktop:/usr/bin$ sudo cp asoundconf /usr/
craig@craig-desktop:/usr/bin$ cd /usr
craig@craig-desktop:/usr$ cp asoundconf /usr/bin/
cp: cannot create regular file `/usr/bin/asoundconf': Permission denied
craig@craig-desktop:/usr$ sudo cp asoundconf /usr/bin/
craig@craig-desktop:/usr$ asoundconf-gtk
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 49, in <module>
    needs_default_card =Live
NameError: name 'Live' is not defined
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
craig@craig-desktop:/usr$

---

### Post by wd5gnr on 2009-12-16
Great guide to a dumb problem ;-)

I did it a little differently

1) Make a temporary directory anywhere and navigate to it in a shell:
 >    mkdir ~/alsa-temp
    cd ~/alsa-temp
Of course, you can make the directory in your favorite graphical way and open a shell on it if you are not as terminal oriented as I am (you are lucky I am not using an ASR33 TTY to do this ;-) ).

2) Go to [http://packages.ubuntu.com/jaunty/alsa-utils](http://packages.ubuntu.com/jaunty/alsa-utils) and download the alsa-utils for your version of ubuntu (i386 or amd64). Save it in the directory you made in #1

3) In the same terminal from #1 run (note, yes type the period at the end of the line):
  >  dpkg -x alsa-utils_1.0.18-1ubuntu11_amd64.deb . 

(or i386 -- whatever you downloaded in #2). Note you do not need sudo for this nor does it install anything.

4) In the terminal type the following (note: DO NOT use a / before usr)
   > cd usr/bin

5) Last command:
   > sudo cp asoundconf /usr/bin

Done! If you are a purist you could copy asoundconf to /usr/local/bin which is probably more appropriate but I fear some script somewhere is hardcoded to look for /usr/bin/asoundconf so I kept it in /usr/bin.

Somehow this seems less stressful on the system to me since you aren't reinstalling and then reinstalling again. But YMMV.

Thanks again. It is a shame there are so many little quirks in Karmic -- it has so many positives that these little flaws really stand out.

6) Oh... one last edit. You can test your installation and remove the temporary directory if you like:
> cd
asoundconf list
rm -r ~/alsa-temp

Be careful with rm -r. If you have doubt, use your GUI tool of choice to delete the directory. Obviously, I'm assuming the 2nd line (asoundconf) produced some meaningful output.

---

### Post by Tumpster on 2009-12-16
craig@craig-desktop:~$ mkdir ~/alsa-temp
craig@craig-desktop:~$ cd ~/alsa-temp
craig@craig-desktop:~/alsa-temp$ dpkg -x alsa-utils_1.0.18-1ubuntu11_i386.deb .
dpkg-deb: failed to read archive `alsa-utils_1.0.18-1ubuntu11_i386.deb': No such file or directory
craig@craig-desktop:~/alsa-temp$ file:///home/craig/Desktop/alsa-utils_1.0.18-1ubuntu11_i386.deb 
bash: file:///home/craig/Desktop/alsa-utils_1.0.18-1ubuntu11_i386.deb: No such file or directory
craig@craig-desktop:~/alsa-temp$ dpkg -x alsa-utils_1.0.18-1ubuntu11_i386.deb .
craig@craig-desktop:~/alsa-temp$ cd usr/bin
craig@craig-desktop:~/alsa-temp/usr/bin$ sudo cp asoundconf /usr/bin
[sudo] password for craig: 
craig@craig-desktop:~/alsa-temp/usr/bin$ cd
craig@craig-desktop:~$ asoundconf list
Names of available sound cards:
Live
craig@craig-desktop:~$ rm -r ~/alsa-temp
craig@craig-desktop:~$ asoundconf
Usage:
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

craig@craig-desktop:~$ asoundconf-gtk
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/craig/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
craig@craig-desktop:~$

---

### Post by wd5gnr on 2009-12-16
Ah. I guess my .asoundrc.asoundconf is still in place for some reason. 

So if you have .asoundrc already and .asoundrc.asoundconf, then you _should_ have a line at the top of .asoundrc that reads:

</home/xxx/.asoundrc.asoundconf>

(where xxx is your user name).

I've manually changed my .asoundrc so I guess the upgrade process didn't munge it. So, as always YMMV. But you can still edit the files in question if you like. But at that point the original process might be just as well.

By the way, the .asoundrc.asoundconf file doesn't have to exist! You just have to make .asoundrc point to it and asoundconf will create it if necessary.

So just for completeness:

7) Open up ~/.asoundrc.asoundconf in your favorite editor (you do NOT need to use sudo). Verify that this line appears near the top:
> </home/XXX/.asoundrc.asoundconf>
If not, add it to the top of the file and save. If it is there, simply exit the editor and you are done.

Still keeps you from having to install and reinstall.

---

### Post by Tumpster on 2009-12-16
> **wd5gnr said:**
> Ah. I guess my .asoundrc.asoundconf is still in place for some reason. 

So if you have .asoundrc already and .asoundrc.asoundconf, then you _should_ have a line at the top of .asoundrc that reads:

</home/xxx/.asoundrc.asoundconf>

(where xxx is your user name).

I've manually changed my .asoundrc so I guess the upgrade process didn't munge it. So, as always YMMV. But you can still edit the files in question if you like. But at that point the original process might be just as well.

By the way, the .asoundrc.asoundconf file doesn't have to exist! You just have to make .asoundrc point to it and asoundconf will create it if necessary.

So just for completeness:

7) Open up ~/.asoundrc.asoundconf in your favorite editor (you do NOT need to use sudo). Verify that this line appears near the top:

If not, add it to the top of the file and save. If it is there, simply exit the editor and you are done.

Still keeps you from having to install and reinstall.

I opened this file up and theres nothing in it. What should be here?

---

### Post by Tumpster on 2009-12-16
I GOT IT! I did some tweaking and creating here and there and got it up and running between editing the files with the directory location and also copy/pasting the above config file he posted for me. With these two I got it up and running. 

BUT what I DON'T have is it actually switching between sound cards on the fly. I told it to swap to my onboard audio and closed out everything running ALSA and it didn't switch, I'm still getting audio from my main card instead of it being mute as it had switched to the onboard as I selected. Every time I bring it up it shows Live as my main one and always comes back to LIve. Ideas?

Here is the output of my files:
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
</home/craig/.asoundrc.asoundconf>
!defaults.pcm.card Live
defaults.ctl.card Live
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.pcm.file_format "raw"
defaults.pcm.file_truncate true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off

Is what my asoundrc.asoundconf and asoundconf show when displayed. ANy ideas?

---

### Post by wd5gnr on 2009-12-16
Great! 

Your .asoundrc should just be:

> </home/craig/.asoundrc.asoundconf>

Unless you know you need any of that other stuff. Otherwise the defaults will just override what asoundconf is doing anyway, I think. Have you tried just that single line in .asoundrc?

---

### Post by Tumpster on 2009-12-28
Alright so here's what I did, I deleted all instances of my asounconf in any form, I uninstalled asoundconf-gtk, and I followed the steps again step by step and instead of trying to run asoundconf-gtk I turned my onboard sound on during a reset and after resetting the machine it works perfectly. Many thanks and I think I just screwed up the previous attempt at this one and just stopped up the drain the more I tried to fix it.

---

### Post by GhodMode on 2010-06-08
I just opened the Jaunty alsa-utils deb file using a file archive utility.  I used Ark, but I'm sure file-roller works as well.  I extracted asoundconf from the deb file to a directory in my path.  It works fine from the command line.

alsa-utils_1.0.18-1ubuntu11_amd64.deb : data.tar.gz : /usr/bin/asoundconf

Don't forget to un-check "Preserve paths when extracting"

Kubuntu 10.04 (Lucid Lynx)

--
-- Ghodmode

---

### Post by cpeachey on 2010-06-26
Thanks for your instructions. I can now select my soundcard! 
Chris

---

### Post by afrodeity on 2010-07-14
Can't believe asoundconf is not being maintained. This is probably why the soundsystem in Ubuntu is so crappy. Its been getting more complicated and worse as time goes by.

The lack of a good alsa configuration utility is what is driving me nuts. 

There are a lot of good apps out there which require customised alsa settings and not having the ability to change between settings, well, name your poison.

Pulseaudio is all find and dandy, but where is the basic architecture of the system? 

Make a noise people.

---

### Post by SpeakingFreely on 2010-09-01
In Jaunty, the file /usr/bin/asoundconf is not compiled.  It is
a python script, text file. I placed it in /usr/bin and
then installed the asoundconf-gtk package.  It works.

Here's the text of the file. You could just copy this, save as 
asoundconf, instead of extracting it from the Jaunty package.  

------starts below this line-------------
#!/usr/bin/python

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

---

### Post by anlag on 2011-06-19
> **SpeakingFreely said:**
> In Jaunty, the file /usr/bin/asoundconf is not compiled.  It is
a python script, text file. I placed it in /usr/bin and
then installed the asoundconf-gtk package.  It works.

Here's the text of the file. You could just copy this, save as 
asoundconf, instead of extracting it from the Jaunty package.  

------starts below this line-------------

...

Thanks for pointing out this significant simplification of the process. However, you would have had to paste it within CODE tags in order to preserve the indentation of the code, since python will not work without adequately indented code blocks.

However, realizing asoundconf was a simple text file made it quite easy to locate a working source of the script:

[http://wiki.marklesh.com/How-to/Asoundconf](http://wiki.marklesh.com/How-to/Asoundconf)

The author of the page mentions having had to modify it to work with newer versions. The page says it's adapted for 10.10, but it works perfectly fine for me also in 11.04. After downloading the asoundconf file (the link is about half way down the page, for the REALLY impatient) it's as simple as making it executable and moving it to /usr/bin:

chmod +x asoundconf
sudo cp -a asoundconf /usr/bin

After which,

asoundconf is-active
asoundconf list
asoundconf set-default-card *cardname*

should enable quick and convenient switching between sound cards. It works like a charm for me, and just to point out in the context that I don't even have a big problem with pulseaudio (nowadays) - it's simply that this is my netbook on which I use the delightfully light weight Lubuntu, which doesn't even have pulseaudio, and STILL does not include asoundconf or any other means I could find to enable me to select my usb speakers as the default audio output. Until now. :-)

---

