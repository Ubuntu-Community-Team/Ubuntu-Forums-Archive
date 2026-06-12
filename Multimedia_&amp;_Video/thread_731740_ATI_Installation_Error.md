---
title: "ATI Installation Error"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by jasonp on 2008-03-22
the screenshot shows the error please help

---

### Post by mikewhatever on 2008-03-22
What do you get from running <sudo aticonfig>?

---

### Post by jasonp on 2008-03-22
> **mikewhatever said:**
> What do you get from running <sudo aticonfig>?
> 
        crt1, lvds, tv, tmds1, crt2, tmds2, cv, tmds2i .
   --query-connectortype=DISPLAYTYPE 
        query the connector type of the specific display.

Component video dongle options:
  Following options are used for query and set dongles for a 
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvdongle
        query dongle setting informations of the component video.
  --set-cvdongle=VALUE
        set the custom override value of the CV dongle. 
  --reset-cvdongle
        reset the custom override setting(to zero)of the CV dongle.

Component video customized mode options:
  Following options are used for query and set customized mode for
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvmode
        query customized modes for component video.
  --add-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEDHEIGHT,REFRESH.
        add a customized mode for component video.
  --validate-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEHEIGHT,REFRESH.
        validate a customized mode for component video.
  --delete-cvmode=INDEX 
        delete one customized mode for component video. 

Persistent Configuration Store (PCS) Options:
  Following options will not change the config file. They are
  used to manipulate the PCS database.  Due to their nature, these.
  commands may only be run by the root user. Note that the prefix
  and key names are not case-sensitive.
  --get-pcs-key=PREFIX,KEY
        Prints out the specified prefix and key from the PCS
        database.  The type of data will be shown along with
        the contents.
  --set-pcs-val=PREFIX,KEY,VALUE
        Sets an integer value at the specified prefix and key in
        the PCS database.  The value may be specified in hex by
        prefixing it with 0x or in octal by prefixing it with 0,
        otherwise the value is assumed to be in decimal.
  --set-pcs-str=PREFIX,KEY,STRING
        Sets a string value at the specified prefix and key in
        the PCS database.
  --set-pcs-raw=PREFIX,KEY,HEXSTRING
        Sets a raw binary value at the specified prefix and key in
        the PCS database.  The value is specified as a series of
        hex bytes with no 0x or spaces.
        (e.g. --set-pcs-raw="TestSection,TestData,E84C0E" sets 3 bytes)
  --del-pcs-key=PREFIX,KEY
        Deletes the specified prefix and key from the PCS database.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup
        Do not make an automatic backup of the configuration file.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv
  5. Change tv geometry 
                         aticonfig --tv-geometry=85x90+10-10 
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre. 


llll
ll

---

### Post by mikewhatever on 2008-03-23
backup the current xorg with <sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup>.
It looks like the fist option is pretty safe to try: <sudo aticonfig --initial --input=/etc/X11/xorg.conf>.

Can you also post the exact model of your video card? <sudo lshw -C display> should provide the required output, otherwise, post <sudo lshw>.

---

### Post by jasonp on 2008-03-23
> **mikewhatever said:**
> backup the current xorg with <sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup>.
It looks like the fist option is pretty safe to try: <sudo aticonfig --initial --input=/etc/X11/xorg.conf>.

Can you also post the exact model of your video card? <sudo lshw -C display> should provide the required output, otherwise, post <sudo lshw>.

cp: cannot stat `/etc/X11/xorg.conf': No such file or directory

--------------------------------------------------------------------------------------------------------

  *-display               
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga bus_master cap_list
       configuration: latency=0

---

### Post by jasonp on 2008-03-23
bump

---

