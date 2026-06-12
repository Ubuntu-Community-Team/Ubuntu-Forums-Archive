---
title: "rename multiple jpg files"
date: 2010-09-10
forum: Multimedia Software
---

### Post by mr.peeters@gmail.com on 2010-09-10
hi, any idea how i could rename multiple jpg files.
say i copied IMG0001.JPG until IMG0134.JPG from my camera, and want to rename IMG0001 until IMG0064.JPG to 'party01.JPG' untill 'party64.JPG', etc.
you see what i mean.
in windows there was a stupid wizard to rename files when you copied them onto your HD from a camera.
is there any good way to do something similar in ubuntu?
thanks

---

### Post by AlphaLexman on 2010-09-10
Here is a 'renamer' python script for Nautlius:
```
#! /usr/bin/python
#  -*- coding: utf-8 -*-

"""
Copyright (C) 2006-2010 Thura Hlaing <trhura@gmail.com>

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License as
published by the Free Software Foundation; either version 3
of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

"""

import os
import sys
import re
import time
import mmap
import string

import pygtk
pygtk.require ('2.0')
import locale, gettext

import gtk
import gobject
import pynotify

# Fake Enums
PATTERNIZE, SUBSTITUTE, CASING, UNDO = range (4)
ALL_CAP, ALL_LOW, FIRST_CAP, EACH_CAP, CAP_AFTER = range (5)
UNDO_LOG_FILE = '.Renamer.log'
LOG_SEP     =  ' is converted to ' # Log file separator
BASE_DIR    =  os.environ.get("HOME") + '/.gnome2/nautilus-scripts/.Renamer.Data/'
ICONS_PATH  =  BASE_DIR + 'icon/'
REC_PATS    = 5 # Remember up to 5 recent patterns
REC_FILE    = 'rec_pats' # filename for recent patterns

# gettext
APP = 'nautilus-renamer'
DIR = BASE_DIR + 'po'

class Application():

    def __init__(self):

        ubox    = gtk.Table (2, 2, True)     # Upper Box
        lframe  = gtk.Frame (_("Options"))
        lalign  = gtk.Alignment ( 0.1, 0.2, 1.0, 0.0)
        self.lbox   = gtk.VBox  (False, 5)  # Lower Box

        # Upper Box Radio Buttons
        pat_rb  = gtk.RadioButton (None,  _("_Patternize"), True)
        sub_rb  = gtk.RadioButton (pat_rb, _("_Substitute"), True)
        cas_rb  = gtk.RadioButton (pat_rb, _("_Case"), True)
        und_rb  = gtk.RadioButton (pat_rb, _("_Undo"), True)

        self.prepare_pat_options (pat_rb)

        lalign.add (self.lbox)
        lalign.set_padding (5, 5, 5, 5)
        lframe.add (lalign)
        lframe.set_size_request (-1, 100)

        #Popup Menu for available patterns
        self.pat_popup  = gtk.Menu ()
        pat_fname   = gtk.MenuItem ('{filename}')
        pat_dir     = gtk.MenuItem ('{dir}')
        pat_name    = gtk.MenuItem ('{name}')
        pat_ext     = gtk.MenuItem ('{ext}')
        pat_day     = gtk.MenuItem ('{day}')
        pat_date    = gtk.MenuItem ('{date}')
        pat_month   = gtk.MenuItem ('{month}')
        pat_year    = gtk.MenuItem ('{year}')
        pat_dname   = gtk.MenuItem ('{dayname}')
        pat_dsimp   = gtk.MenuItem ('{daysimp}')
        pat_mname   = gtk.MenuItem ('{monthname}')
        pat_msimp   = gtk.MenuItem ('{monthsimp}')
        pat_num1    = gtk.MenuItem ('{num2}')
        pat_num2    = gtk.MenuItem ('{num3+0}')
        
        # TODO: Write explanations (tooltips) for the patterns above.
        # e.g., pat_fname.set_tooltip_text ("{filename} explanation")

        self.pat_popup.attach (pat_fname,   0, 1, 0, 1)
        self.pat_popup.attach (pat_dir,     1, 2, 0, 1)
        self.pat_popup.attach (pat_name,    0, 1, 1, 2)
        self.pat_popup.attach (pat_ext,     1, 2, 1, 2)
        self.pat_popup.attach (pat_day,     0, 1, 2, 3)
        self.pat_popup.attach (pat_date,    1, 2, 2, 3)
        self.pat_popup.attach (pat_month,   0, 1, 3, 4)
        self.pat_popup.attach (pat_year,    1, 2, 3, 4)
        self.pat_popup.attach (pat_dname,   0, 1, 4, 5)
        self.pat_popup.attach (pat_dsimp,   1, 2, 4, 5)
        self.pat_popup.attach (pat_mname,   0, 1, 5, 6)
        self.pat_popup.attach (pat_msimp,   1, 2, 5, 6)
        self.pat_popup.attach (pat_num1,    0, 1, 6, 7)
        self.pat_popup.attach (pat_num2,    1, 2, 6, 7)

        self.pat_popup.show_all ()

        ubox.attach (pat_rb, 0, 1, 0, 1, gtk.EXPAND | gtk.FILL, gtk.EXPAND | gtk.FILL, 0)
        ubox.attach (sub_rb, 1, 2, 0, 1, gtk.EXPAND | gtk.FILL, gtk.EXPAND | gtk.FILL, 0)
        ubox.attach (cas_rb, 0, 1, 1, 2, gtk.EXPAND | gtk.FILL, gtk.EXPAND | gtk.FILL, 0)
        ubox.attach (und_rb, 1, 2, 1, 2, gtk.EXPAND | gtk.FILL, gtk.EXPAND | gtk.FILL, 0)

        self.dialog = gtk.Dialog ("Renamer", None, gtk.DIALOG_NO_SEPARATOR,
                                  (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OK, gtk.RESPONSE_OK))
        
        self.recur_cb = gtk.CheckButton (_("_Recursive"), True)
        self.ext_cb   = gtk.CheckButton (_("_Extension"), True)  

        bbox    = gtk.HBox (False, 5);

        bbox.pack_end (self.recur_cb, False, True, 0)
        bbox.pack_end (self.ext_cb, False, True, 0)

        ralign = gtk.Alignment (1.0, 0.5, 0.0, 0.0)
        ralign.add (bbox)

        mbox    = gtk.VBox ( False, 10)
        mbox.pack_start (ubox, False, True, 0)
        mbox.pack_start (lframe, True, True, 0)
        mbox.pack_end   (ralign, False, False, 0)

        malign = gtk.Alignment (0.0, 0.0, 1.0, 0.0)
        malign.set_padding (10, 10, 10, 10)

        malign.add (mbox)
        self.dialog.vbox.add (malign)

        self.dialog.set_default_size (380, 220)
        self.dialog.set_icon_from_file (ICONS_PATH + 'renamer.png')
        self.dialog.show_all ()

        pat_rb.connect ('toggled', self.prepare_pat_options)
        sub_rb.connect ('toggled', self.prepare_sub_options)
        cas_rb.connect ('toggled', self.prepare_cas_options)
        und_rb.connect ('toggled', self.prepare_und_options)

        pat_dir.connect   ('activate', self.on_popup_activate)
        pat_ext.connect   ('activate', self.on_popup_activate)
        pat_day.connect   ('activate', self.on_popup_activate)
        pat_date.connect  ('activate', self.on_popup_activate)
        pat_name.connect  ('activate', self.on_popup_activate)
        pat_year.connect  ('activate', self.on_popup_activate)
        pat_fname.connect ('activate', self.on_popup_activate)
        pat_month.connect ('activate', self.on_popup_activate)
        pat_dname.connect ('activate', self.on_popup_activate)
        pat_dsimp.connect ('activate', self.on_popup_activate)
        pat_mname.connect ('activate', self.on_popup_activate)
        pat_msimp.connect ('activate', self.on_popup_activate)
        pat_num1.connect ('activate', self.on_popup_activate)
        pat_num2.connect ('activate', self.on_popup_activate)

        self.case_opt = ALL_CAP
        self.recur    = False
        self.ext      = False
        self.pattern  = None
        self.logFile  = None
        self.num = 0
        self.num_pat = re.compile(r'(\{num\d*\}|(\{num\d*\+\d*\}))')
        self.filesRenamed = 0

    def prepare_pat_options (self, button, data=None):

        if not button.get_active():
            return

        self.lbox.foreach (self.remove)
        self._read_recent_pats ()

        hbox    = gtk.HBox (False, 5)

        combo   = gtk.ComboBoxEntry (self.pats, 0)
        self.pat_entry  = combo.child
        button  = gtk.Button (" _?", None, True)
        label   = gtk.Label (_("For descriptions of available patterns, read README."))
        label.set_line_wrap (True)

        self.pat_entry.label = _("Enter the pattern here ... ")
        self.prepare_entry (self.pat_entry)

        hbox.pack_start (combo, True, True, 0)
        hbox.pack_start (button, False, False, 0)

        button.connect ('button-press-event', lambda button, event:
                            self.pat_popup.popup (None, None, None, event.button, event.time))

        combo.connect ('changed', self.combo_box_changed )
                              
        self.pat_entry.connect ('activate', self.pat_entry_activate)

        self.lbox.pack_start (label, True, True, 0)
        self.lbox.pack_start (hbox, True, True, 0)
        self.lbox.show_all ()

        self.action = PATTERNIZE

    def combo_box_changed (self, combo, data=None):
        "When patten combo box entry is changed"
        combo.child.clr_on_focus = False

    def pat_entry_activate (self, entry, data=None):
        "When Return is pressed on pattern entry"
        self.rename (files)
        self.dialog.destroy ()

    def prepare_sub_options (self, button, data=None):

        if not button.get_active():
            return

        self.lbox.foreach (self.remove)

        self.sub_replee = gtk.Entry ()
        self.sub_replee.label =  _("Enter the word (phrase) to be replaced here ...")
        self.prepare_entry (self.sub_replee)

        self.sub_repler = gtk.Entry ()
        self.sub_repler.label = _("Enter the word to replace with here ... ")
        self.prepare_entry (self.sub_repler)

        self.lbox.pack_start (self.sub_replee, True, True, 0)
        self.lbox.pack_start (self.sub_repler, True, True, 0)

        self.lbox.show_all ()

        self.action = SUBSTITUTE

    def prepare_cas_options (self, button, data=None):

        if not button.get_active ():
            return

        self.lbox.foreach (self.remove)

        store   = gtk.ListStore ('gboolean', str, int)

        store.append([True,  _("ALL IN CAPITALS"), ALL_CAP])
        store.append([False, _("all in lower case"), ALL_LOW])
        store.append([False, _("First letter upper case"), FIRST_CAP])
        store.append([False, _("Title Case"), EACH_CAP])
        store.append([False, _("Capital Case After ..."), CAP_AFTER])

        self.view   = gtk.TreeView (store)
        self.view.set_rules_hint (True)

        cell    = gtk.CellRendererToggle ()
        cell.set_radio (True)
        cell.set_property ('xalign', 0.1)

        column  = gtk.TreeViewColumn ()
        column.pack_start (cell, False)
        column.set_sizing (gtk.TREE_VIEW_COLUMN_FIXED)
        column.set_fixed_width (40)
        column.add_attribute (cell, 'active', 0)

        self.view.append_column (column)

        cell    = gtk.CellRendererText ()
        cell.set_property ('scale', 0.9)

        column  = gtk.TreeViewColumn(_("Choose One"))
        column.pack_start (cell, True)
        column.add_attribute (cell, 'text', 1)

        self.view.append_column (column)

        self.scroll_win  = gtk.ScrolledWindow()
        self.scroll_win.set_policy (gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.scroll_win.add(self.view)

        self.view.connect ('cursor-changed', self.cursor_changed)
        self.lbox.pack_start (self.scroll_win, True, True, 0)
        self.lbox.show_all ()

        self.action  = CASING

    def prepare_und_options (self, button, data=None):

        if not button.get_active ():
            return

        self.lbox.foreach (self.remove)

        und_label = gtk.Label ()
        und_label.set_line_wrap (True)
        und_label.set_alignment (0.1, 0.5)
        und_label.set_markup (_("<b>Undo the last operation inside this folder.\n\n</b>" +
                                   "<small>Note: You cannot undo an undo. ;)</small>"))

        self.lbox.pack_start (und_label, True, True, 0)
        self.lbox.show_all ()

        self.action = UNDO
    
    def prepare_cap_after_options (self):
        
        self.scroll_win.remove (self.view)
        self.lbox.remove (self.scroll_win)

        cap_label = gtk.Label (_("Capitalize after: "))

        self.cap_entry = gtk.Entry ()
        self.cap_entry.set_text (' /-/_/[/(')
        self.cap_first = gtk.CheckButton (_("_First Letter"), True)        
        self.cap_first.set_active (False)
        
        cbox    = gtk.Table (3, 2, False)
        cbox.attach (cap_label, 0, 1, 0, 1, 0)
        cbox.attach (self.cap_entry, 1, 2, 0, 1, gtk.EXPAND | gtk.FILL, gtk.EXPAND | gtk.FILL, 2, 5)
        cbox.attach (self.cap_first, 1, 2, 1, 2, gtk.EXPAND | gtk.FILL, gtk.EXPAND | gtk.FILL)

        self.lbox.pack_start (cbox, True, True, 0)

        self.cap_entry.set_tooltip_text (_("Enter the list of sequences, to capitalize the letter after each of it, separated by '/'"))
        self.cap_first.set_tooltip_text (_("Capitalize the first letter"))
        self.lbox.show_all ()
        
    def prepare_entry (self, entry):
        """ Helper function for preparing entries in our dialog """
        entry.clr_on_focus = True   # Clear current text when the entry is focused
        entry.set_text (entry.label)
        entry.modify_text(gtk.STATE_NORMAL, gtk.gdk.Color('#4C4C4C'))
        entry.connect ('focus-in-event',  self.entry_focus_in)
        entry.connect ('focus-out-event', self.entry_focus_out)

    def entry_focus_in (self, widget, event, data=None):
        """ When the entriy is focused for the first time, clear the label text, and reset text color. """
        if widget.clr_on_focus:
            widget.set_text ("")
            widget.modify_text(gtk.STATE_NORMAL, gtk.gdk.Color('#000000'))
            widget.clr_on_focus = False

    def entry_focus_out (self, widget, event, data=None):
        """ When the entry focus is out without any changes, restore label text and color."""
        if widget.get_text () == "":
            self.prepare_entry (widget)

    def on_popup_activate (self, item, data=None):
        """ When a menutitem on patterns popup menu is clicked, append the label to pattern entry. """
        self.entry_focus_in (self.pat_entry, None, None)
        self.pat_entry.set_text (self.pat_entry.get_text() + item.get_property('label'))

    def cursor_changed (self, treeview, data=None):
        """ When selected row in CASE tree view is changed, update the tree model. """
        model, iter = treeview.get_selection().get_selected ()
        model.foreach (lambda model, path, iter: model.set (iter, 0, False))
        model.set (iter, 0, True)
        self.case_opt = model.get_value (iter, 2)
        
        if self.case_opt == CAP_AFTER:
            self.prepare_cap_after_options ()

    def remove (self, child):
        """ callback to remove a child from lbox """
        self.lbox.remove (child)

    def rename (self, files):
        """ Wrapper around _rename (). Prepare and validate settings for renaming, and start log """
        if self.action == UNDO:
            self.undo ()
            return
            
        if not files:
            #no files to rename ?
            self.notify (_("No file selected"), _("Dude, select some files first."), ICONS_PATH + 'info.png', 5000)
            return

        self.recur = self.recur_cb.get_active ()
        self.ext   = self.ext_cb.get_active ()        

        if self.action == PATTERNIZE:
            # prepare patternize related options, and check for possible errors
            self.pattern = self.pat_entry.get_text ()

            if self.pattern == '' or self.pattern == self.pat_entry.label:
                print self.pat_entry.get_text ()
                self.notify (_("Empty Pattern"), _("Please, enter a valid pattern."), ICONS_PATH + 'error.png', 5000)
                return

            if self.num_pat.search(self.pattern):
                #if the pattern contains {num*} or {num*+*}, disable recursion
                self.recur = False

            if not self.num_pat.search(self.pattern) and self.pattern.find ('{filename') == -1 and self.pattern.find ('{name}') == -1 and len(files) > 1:
                # If the pattern doesn't contain any of {num3} {num3+3} {filename} {name}, abort renaming
                # As it will try to rename all input files into one name.
                self.notify(_("Operation Aborted!"), _("Renamer is trying to rename multiple files into one. The pattern should contain at least one of {num * } , {filename} or {name}"),
                ICONS_PATH  + 'warning.png',5000)
                return

        elif self.action == SUBSTITUTE:
            # prepare substitute related options, and check for possible errors
            self.replee = self.sub_replee.get_text ()
            self.repler = self.sub_repler.get_text ()

            if self.replee == self.sub_replee.label or self.replee == '':
                self.notify(_("Get a brain!"),_("come on, you can't replace nothing with something."),
                ICONS_PATH  + 'warning.png',5000)
                return
            if self.repler == self.sub_repler.label:
                self.repler = ''

        self.start_log ()

        for file in files:
            app._rename(file)

        self.close_log ()
        
        if self.action == PATTERNIZE:
            self._write_recent_pats ()

        self.notify(_("Rename successful"), _("renamed %d files successfully.") % self.filesRenamed, ICONS_PATH  + 'success.png',5000)

    def _rename (self, path, oldPath=''):
        """ recursive function to rename """
        parent, oldName = os.path.split (path)
        newName = self._get_new_name (oldName)
        newPath = os.path.join (parent, newName)
        oldPath = os.path.join (oldPath, oldName)

        if not path == newPath:
            os.rename (path, newPath)
            self.logFile.write ('%s%s%s\n' %(oldPath, LOG_SEP,newPath))
            self.filesRenamed = self.filesRenamed + 1

        if  os.path.isdir(newPath) and self.recur:
            for file in os.listdir (newPath):
                self._rename (os.path.join (newPath, file), oldPath)
                
    def _write_recent_pats (self):
        """ Store recent patterns """
        with open (BASE_DIR + REC_FILE, 'w') as file:
            i = 1
            cpat = self.pat_entry.get_text()
            file.write (cpat + '\n' ) 
            for pat in self.pats:
                if i < REC_PATS and not pat[0] == cpat:
                    file.write (pat[0] + '\n')
                    i = i + 1

    def _read_recent_pats (self):
        """ Read recent patterns """
        self.pats = gtk.ListStore (gobject.TYPE_STRING)

        try:
            with open (BASE_DIR + REC_FILE, 'r') as file:
                for pat in file:
                    self.pats.append ([pat[:-1]])
        except:
            pass
				
    def _get_new_name (self, oldName):
        """ return a new name, based on the old name, and settings from our dialog. """

        if oldName.startswith('.'):
        # Exclude hidden files, what else to exculde?
            return oldName

        if self.action == SUBSTITUTE:
            #TODO: Regex Support ?
            if self.ext:
                return oldName.replace (self.replee, self.repler)
            else:
                name, ext = os.path.splitext (oldName)
                return name.replace (self.replee, self.repler ) + ext               

        if self.action == CASING:
            if self.ext:
                name = oldName
            else:
                name, ext = os.path.splitext (oldName)

            if self.case_opt == ALL_CAP:
                name = name.upper ()

            elif self.case_opt == ALL_LOW:
                name = name.lower()

            elif self.case_opt == FIRST_CAP:
                name = name.capitalize()

            elif self.case_opt == EACH_CAP:
                name = name.title ()
                
            elif self.case_opt == CAP_AFTER:
                
                if self.cap_first.get_active():
                    name = name.capitalize()
            
                seps  = self.cap_entry.get_text ()

                for sep in seps.split ('/'):
                    lst = [ l for l in name.split(sep)]
                    for i in xrange(1, len(lst)):
                        if lst[i] is not '':
                            lst[i] = lst[i][0].upper() + lst[i][1:]
                    name = sep.join (lst)
        
            if self.ext:
                return name
            else:
                return name + ext


        if self.action == PATTERNIZE:

            newName = self.pattern

            #for number substiution
            if self.num_pat.search(newName):
                tmp = self.num_pat.search(newName).group()
                #if {num?}
                if len(tmp)== 6:
                    substitute = str(self.num).zfill(int(tmp[4]))
                    newName    = self.num_pat.sub(substitute, newName)
                    self.num   = self.num + 1
                #if {num?+?}
                elif len(tmp) > 7:
                    substitute = str(self.num+int(tmp[6:(len(tmp)-1)])).zfill(int(tmp[4]))
                    newName    = self.num_pat.sub(substitute, newName)
                    self.num   = self.num + 1

            dir, file = os.path.split (oldName)
            name, ext = os.path.splitext (file)

            #replace filename related Tags
            newName = newName.replace('{filename}',oldName)
            newName = newName.replace('{dir}', dir)
            newName = newName.replace('{name}', name)
            newName = newName.replace('{ext}', ext)

            #Some Time/Date Replacements
            newName = newName.replace('{date}', time.strftime('%d%b%Y', time.localtime()))
            newName = newName.replace('{year}', time.strftime('%Y', time.localtime()))
            newName = newName.replace('{month}', time.strftime('%m', time.localtime()))
            newName = newName.replace('{monthname}', time.strftime('%B', time.localtime()))
            newName = newName.replace('{monthsimp}', time.strftime('%b', time.localtime()))
            newName = newName.replace('{day}', time.strftime('%d', time.localtime()))
            newName = newName.replace('{dayname}', time.strftime('%A', time.localtime()))
            newName = newName.replace('{daysimp}', time.strftime('%a', time.localtime()))

            return newName

    def undo (self):
        """ renames files back according to the log file. """

        try:
            logFile = open (UNDO_LOG_FILE, 'rb')
        except IOError:
            self.notify(_("Log file not found"),_("You must be in the same folder, where you use Renamer, to undo."), ICONS_PATH  + 'error.png',5000)
            sys.exit(1)

        for i in range(5): logFile.readline () #Skip 5 lines of header

        for line in logFile:
            oldpath, newpath = line.split('\n')[0].split(LOG_SEP)
            os.rename(os.path.join(os.path.dirname(oldpath),os.path.basename(newpath)),oldpath)
            self.filesRenamed = self.filesRenamed + 1

        logFile.close ()

        os.remove (UNDO_LOG_FILE)
        self.notify(_("Undo successful"),_("%d files restored.") % self.filesRenamed, ICONS_PATH  + 'success.png',5000)

    def start_log (self):
        """ Open log and write header. """
        self.logFile = open (UNDO_LOG_FILE, 'wb', 1)

        self.logFile.write (' Renamer Log '.center (80, '#'))
        self.logFile.write ('\n')

        self.logFile.write ('# File :  files\n')
        self.logFile.write ('# Time : ')
        self.logFile.write (time.strftime('%a, %d %b %Y %H:%M:%S\n'))
        self.logFile.write ('#'.center (80, '#'))
        self.logFile.write ('\n\n')

    def close_log (self):
        """ Close log file, and insert total file renamed."""
        self.logFile.close ()

        with open (UNDO_LOG_FILE, 'r+b') as file:
            m = mmap.mmap(file.fileno(), os.path.getsize(UNDO_LOG_FILE))
            str = '%d' % self.filesRenamed
            l = len(str) #len
            s = m.size() #size
            o = 90       #offset
            m.resize (s + l)
            m[(o+l) : ] = m [o : s]
            m[o : (o+l)] = str
            m.close ()

    def notify(self, title,text,iconpath,time):
        """ Wrapper to display notifications with timeout time. """
        if not pynotify.init("Renamer"):
            sys.exit(1)

        n = pynotify.Notification(title,text,iconpath)
        n.set_timeout(time)

        if not n.show():
            print "Failed to send notification"
            sys.exit(1)

def init_gettext ():

	langs = []
	lc, encoding = locale.getdefaultlocale()
	
	if(lc):
		langs = [lc]
	
	language = os.environ.get('LANGUAGE', None)
	if(language): 
		langs += language.split(':')
		
	langs += ['en_US', 'de_DE']
	
	gettext.bindtextdomain(APP, DIR)
	gettext.textdomain(APP) 
	
	lang = gettext.translation (APP, DIR, languages=langs, fallback=True)
	_ = lang.gettext
	gettext.install (APP, DIR)
	
if __name__ == '__main__':
	
	init_gettext ()
	files = [file for file in sys.argv[1:]]
	
	app = Application ()
	ret = app.dialog.run ()
	
	if ret == gtk.RESPONSE_OK:
		app.rename (files)




```
Just save it as 'Renamer' and make it executable in [ ~/.gnome2/nautilus-scripts/ ]

---

