---
title: "Name of utilities that will generate your xorg.conf?"
date: 2009-05-04
forum: Multimedia Software
---

### Post by jeeves on 2009-05-04
I remember once using a Nvidia utility that would generate a new xorg.conf file for a Nvidia card.  Does anyone know the name of that little program?

Also, I think Ubuntu had a similar utility built in, but it would do a generic xorg.conf file.  Anyone know the name for that utility as well?

---

### Post by darkscout on 2009-05-04
> **jeeves said:**
> I remember once using a Nvidia utility that would generate a new xorg.conf file for a Nvidia card.  Does anyone know the name of that little program?

Also, I think Ubuntu had a similar utility built in, but it would do a generic xorg.conf file.  Anyone know the name for that utility as well?
[B]
nvidia-settings [/B]
```
nvidia-settings:  version 1.0  (buildmeister@builder63)  Thu Apr 16 19:37:21
PDT 2009
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.

  Copyright (C) 2004 - 2008 NVIDIA Corporation.


nvidia-settings [options]

  -v, --version
      Print the nvidia-settings version and exit.

  -h, --help
      Print usage information and exit.

  --config=[CONFIG]
      Use the configuration file [CONFIG] rather than the default
      ~/.nvidia-settings-rc

  -c, --ctrl-display=[CTRL-DISPLAY]
      Control the specified X display.  If this option is not given, then
      nvidia-settings will control the display specifed by '--display'.  If
      that is not given, then the $DISPLAY environment variable is used.

  -l, --load-config-only
      Load the configuration file, send the values specified therein to the X
      server, and exit.  This mode of operation is useful to place in your
      .xinitrc file, for example.

  -n, --no-config
      Do not load the configuration file.  This mode of operation is useful if
      nvidia-settings has difficulties starting due to problems with applying
      settings in the configuration file.

  -r, --rewrite-config-file
      Write the X server configuration to the configuration file, and exit,
      without starting the graphical user interface.

  -V, --verbose=[VERBOSE]
      Controls how much information is printed.  Valid values are 'errors'
      (print error messages), 'warnings' (print error and warning messages),
      and 'all' (print error, warning and other informational messages).  By
      default, only errors are printed.

  -a, --assign=[ASSIGN]
      The ASSIGN argument to the '--assign' commandline option is of the form:

        {DISPLAY}/{attribute name}[{display devices}]={value}

      This assigns the attribute {attribute name} to the value {value} on the X
      Display {DISPLAY}.  {DISPLAY} follows the usual {host}:{display}.{screen}
      syntax of the DISPLAY environment variable and is optional; when it is
      not specified, then it is implied following the same rule as the
      --ctrl-display option.  If the X screen is not specified, then the
      assignment is made to all X screens.  Note that the '/' is only required
      when {DISPLAY} is present.

      {DISPLAY} can additionally include a target specification to direct an
      assignment to something other than an X screen.  A target specification
      is contained within brackets and consists of a target type name, a colon,
      and the target id.  The target type name can be one of "screen", "gpu",
      or "framelock"; the target id is the index into the list of targets (for
      that target type).  The target specification can be used in {DISPLAY}
      wherever an X screen can be used, following the syntax
      {host}:{display}[{target_type}:{target_id}].  See the output of
      `nvidia-settings -q all` for information on which target types can be
      used with which attributes.  See the output of `nvidia-settings -q
      screens -q gpus -q framelocks` for lists of targets for each target
      type.

      The [{display devices}] portion is also optional; if it is not specified,
      then the attribute is assigned to all display devices.

      Some examples:

        -a FSAA=5
        -a localhost:0.0/DigitalVibrance[CRT-0]=0
        --assign="SyncToVBlank=1"
        -a [gpu:0]/DigitalVibrance[DFP-1]=63

  -q, --query=[QUERY]
      The QUERY argument to the '--query' commandline option is of the form:

        {DISPLAY}/{attribute name}[{display devices}]

      This queries the current value of the attribute {attribute name} on the X
      Display {DISPLAY}.  The format is the same as that for the '--assign'
      option, without '={value}'.  Specify '-q screens', '-q gpus', or '-q
      framelocks' to query a list of X screens, GPUs, or Frame Lock devices,
      respectively, that are present on the X Display {DISPLAY}.  Specify '-q
      all' to query all attributes.

  -t, --terse
      When querying attribute values with the '--query' commandline option,
      only print the current value, rather than the more verbose description of
      the attribute, its valid values, and its current value.

  -d, --display-device-string
      When printing attribute values in response to the '--query' option, if
      the attribute value is a display device mask, print the value as a list
      of display devices (e.g., "CRT-0, DFP-0"), rather than a hexidecimal
      bitmask (e.g., 0x00010001).

  -g, --glxinfo
      Print GLX Information for the X display and exit.

  -e, --describe=[DESCRIBE]
      Prints information about a particular attribute.  Specify 'all' to list
      the descriptions of all attributes.  Specify 'list' to list the attribute
      names without a descriptions.
```& 


**nvidia-xconfig**
```
nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Thu Apr 16 19:36:29 PDT
2009
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 - 2008 NVIDIA Corporation.


  In its normal operation, nvidia-xconfig finds the system X configuration file
  (or generates a new X configuration if it cannot find the system file), makes
  sure the configuration is usable by the NVIDIA X driver, applies any updates
  requested on the commandline, and writes the new configuration to file.

  Please see the NVIDIA README for a description of NVIDIA X configuration file
  options.


nvidia-xconfig [options]

  -c XCONFIG, --xconfig=XCONFIG
      Use XCONFIG as the input X config file; if this option is not specified,
      then the same search path used by the X server will be used to find the X
      configuration file.

  -o OUTPUT-XCONFIG, --output-xconfig=OUTPUT-XCONFIG
      Use OUTPUT-XCONFIG as the output X configuration file; if this option is
      not specified, then the input X configuration filename will also be used
      as the output X configuration filename.

  -s, --silent
      Run silently; no messages will be printed to stdout, except for warning
      and error messages to stderr.

  -t, --tree
      Read the X configuration file, print to stdout the X configuration data
      in a tree format, and exit.

  -v, --version
      Print the nvidia-xconfig version and exit.

  -h, --help
      Print usage information for the common commandline options and exit.

  -A, --advanced-help
      Print usage information for the common commandline options as well as the
      advanced options, and then exit.

```

---

### Post by 67GTA on 2009-05-04
```
sudo nvidia-xconfig
``` is probably what you want. It will try to create a new xorg.conf file with your nvidia settings merged in.

---

