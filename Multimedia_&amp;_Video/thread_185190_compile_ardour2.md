---
title: "compile ardour2"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by hanzomon4 on 2006-05-31
I need help building ardour from source, I don't see a configure, or make file.

---

### Post by Sef on 2006-05-31
> I need help building ardour from source, I don't see a configure, or make file.

To compile, you need build-essential.

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install build-essential

---

### Post by hanzomon4 on 2006-05-31
Okay I almost have it, Ardour2 uses an SConstruct file. 

So I ran scons and got this
> hanzomon4@EIDOKIN:~/trunk$ scons
scons: Reading SConscript files ...
Checking for usb_interrupt_write() in C library usb... yes
Checking for lo_server_new() in C library lo... yes
Checking for dmalloc_shutdown() in C library dmallocth... no
Checking for C header file alsa/asoundlib.h... no
Checking for C header file /System/Library/Frameworks/CoreMIDI.framework/Headers/CoreMIDI.h... no
Congratulations, you have a functioning C++ compiler.
system triple: i686-pc-linux-gnu

*******************************
detected DIST_TARGET = i686
*******************************

Checking for internationalization support ...
Checking for C header file libintl.h... yes
Checking for C header file /System/Library/Frameworks/CoreAudio.framework/Versions/A/Headers/CoreAudio.h... no
Checking for C function posix_memalign()... yes
Checking for C function getmntent()... yes
Checking for C header file execinfo.h... yes
KeyError: 'SYSMIDI':
  File "SConstruct", line 861:
    SConscript (subdir + '/SConscript')
  File "/usr/lib/python2.4/site-packages/SCons/Script/SConscript.py", line 581:
    return apply(method, args, kw)
  File "/usr/lib/python2.4/site-packages/SCons/Script/SConscript.py", line 508:
    return apply(_SConscript, [self.fs,] + files, {'exports' : exports})
  File "/usr/lib/python2.4/site-packages/SCons/Script/SConscript.py", line 239:
    exec _file_ in stack[-1].globals
  File "libs/midi++2/SConscript", line 37:
    if env['SYSMIDI'] == 'CoreMIDI':
  File "/usr/lib/python2.4/site-packages/SCons/Environment.py", line 290:
    return self._dict[key]

Any idea what I am doing wrong

---

### Post by hanzomon4 on 2006-05-31
Okay I solved last problem by installind the asound-dev package.

But now I get this error

> libs/glibmm2/glibmm/ustring.h:32:26: error: glibmmconfig.h: No such file or directory
libs/glibmm2/glibmm/ustring.h:33: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/exception.h:35: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/error.h:38: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/error.h:38: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/error.h:38: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/error.h:48: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/value.h:95: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/value.h:95: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/value.h:95: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/value.h:113: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/value.h:113: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/value.h:113: error: ISO C++ forbids declaration of 'parameter' with no typelibs/glibmm2/glibmm/value.h:133: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/value.h:133: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/value.h:133: error: ISO C++ forbids declaration of 'parameter' with no typelibs/glibmm2/glibmm/value.h:152: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/value.h:152: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/value.h:152: error: ISO C++ forbids declaration of 'parameter' with no typelibs/glibmm2/glibmm/value.h:171: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/value.h:171: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/value.h:171: error: ISO C++ forbids declaration of 'parameter' with no typelibs/glibmm2/glibmm/value_custom.h:31: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/value_basictypes.h:23: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:24: error: explicit specialization of non-template 'Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:35: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/value_basictypes.h:35: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/value_basictypes.h:44: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:44: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:44: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:65: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:65: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:65: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:86: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:86: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:86: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:107: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:107: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:107: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:128: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:128: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:128: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:149: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:149: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:149: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:170: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:170: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:170: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:191: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:191: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:191: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:212: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:212: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:212: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:233: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:233: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:233: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:254: error: 'Value' is not a template
libs/glibmm2/glibmm/value_basictypes.h:254: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value_basictypes.h:254: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value.h:266: error: 'Value' is not a template
libs/glibmm2/glibmm/value.h:266: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value.h:266: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/value.h:279: error: 'Value' is not a template
libs/glibmm2/glibmm/value.h:279: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/value.h:279: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/value.h:279: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/value.h:279: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/propertyproxy.h: In member function 'void Glib::PropertyProxy<T>::set_value(const T&)':
libs/glibmm2/glibmm/propertyproxy.h:140: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/propertyproxy.h:141: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/propertyproxy.h:141: error: expected primary-expression before '::' token
libs/glibmm2/glibmm/propertyproxy.h: In member function 'T Glib::PropertyProxy<T>::get_value() const':
libs/glibmm2/glibmm/propertyproxy.h:150: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/propertyproxy.h:151: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/propertyproxy.h:151: error: expected primary-expression before '::' token
libs/glibmm2/glibmm/objectbase.h: At global scope:
libs/glibmm2/glibmm/objectbase.h:31: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/objectbase.h:86: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/objectbase.h:86: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/objectbase.h:86: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/objectbase.h:89: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/objectbase.h:89: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/objectbase.h:89: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/objectbase.h:93: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/objectbase.h:93: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/objectbase.h:93: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/objectbase.h:97: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/objectbase.h:97: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/objectbase.h:97: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/objectbase.h:142: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/objectbase.h:142: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/objectbase.h:142: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/objectbase.h: In member function 'void Glib::ObjectBase::set_property(int)':
libs/glibmm2/glibmm/objectbase.h:144: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/objectbase.h:145: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/objectbase.h:145: error: expected primary-expression before '::' token
libs/glibmm2/glibmm/objectbase.h:147: error: 'value' was not declared in this scope
libs/glibmm2/glibmm/objectbase.h:148: error: 'property_name' was not declared in this scope
libs/glibmm2/glibmm/objectbase.h: At global scope:
libs/glibmm2/glibmm/objectbase.h:152: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/objectbase.h:152: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/objectbase.h:152: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/objectbase.h: In member function 'void Glib::ObjectBase::get_property(int) const':
libs/glibmm2/glibmm/objectbase.h:154: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/objectbase.h:155: error: 'Glib::Value' is not a template
libs/glibmm2/glibmm/objectbase.h:155: error: expected primary-expression before '::' token
libs/glibmm2/glibmm/objectbase.h:157: error: 'property_name' was not declared in this scope
libs/glibmm2/glibmm/objectbase.h:159: error: 'value' was not declared in this scope
libs/glibmm2/glibmm/quark.h: At global scope:
libs/glibmm2/glibmm/quark.h:49: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/quark.h:49: error: ISO C++ forbids declaration of 'ustring' with no type
libs/glibmm2/glibmm/quark.h:53: error: expected type-specifier before 'ustring'
libs/glibmm2/glibmm/quark.h:65: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/quark.h:65: error: ISO C++ forbids declaration of 'ustring' with no type
libs/glibmm2/glibmm/quark.h:81: error: 'GLIBMM_API' does not name a type
libs/glibmm2/glibmm/quark.h:82: error: 'GLIBMM_API' does not name a type
libs/glibmm2/glibmm/utility.h:82: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/utility.h:96: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/containerhandle_shared.h:39: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/object.h:163: error: 'TypeTraits' is not a template
libs/glibmm2/glibmm/object.h:233: error: expected initializer before '<' token
libs/glibmm2/glibmm/object.h:243: error: 'Value' is not a template
libs/glibmm2/glibmm/object.h:243: error: 'Glib::Value' is not a template type
libs/glibmm2/glibmm/object.h:243: error: redefinition of 'class Glib::Value'
libs/glibmm2/glibmm/value_basictypes.h:24: error: previous definition of 'class Glib::Value'
libs/glibmm2/glibmm/convert.h:64: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/convert.h:64: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/convert.h:64: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/convert.h:190: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/convert.h:190: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/convert.h:190: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/convert.h:199: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/convert.h:208: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/convert.h:208: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/convert.h:208: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/convert.h:216: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/convert.h:223: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/convert.h:223: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/convert.h:223: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/convert.h:233: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/convert.h:233: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/convert.h:233: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/convert.h:241: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/convert.h:241: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/convert.h:241: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/convert.h:250: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/convert.h:258: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/convert.h:274: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/convert.h:291: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/date.h:119: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/date.h:119: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/date.h:119: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/date.h:334: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/fileutils.h:37: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/main.h:34: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/iochannel.h:37: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/iochannel.h:144: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/iochannel.h:144: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/iochannel.h:144: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/iochannel.h:305: error: 'Glib::ustring' has not been declared
libs/glibmm2/glibmm/iochannel.h:315: error: 'Glib::ustring' has not been declared
libs/glibmm2/glibmm/iochannel.h:325: error: 'Glib::ustring' has not been declared
libs/glibmm2/glibmm/iochannel.h:337: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/iochannel.h:337: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/iochannel.h:337: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/iochannel.h:554: error: 'IOCondition' does not name a type
libs/glibmm2/glibmm/iochannel.h:648: error: 'IOCondition' has not been declared
libs/glibmm2/glibmm/iochannel.h:680: error: 'IOCondition' has not been declared
libs/glibmm2/glibmm/markup.h:33: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/markup.h:92: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:92: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:92: error: ISO C++ forbids declaration of 'parameter' with no typelibs/glibmm2/glibmm/markup.h:146: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/markup.h:213: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/markup.h:214: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/markup.h:217: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:217: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:217: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/markup.h:242: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/markup.h:242: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/markup.h:242: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/markup.h:242: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/markup.h:242: error: template argument 1 is invalid
libs/glibmm2/glibmm/markup.h:242: error: template argument 2 is invalid
libs/glibmm2/glibmm/markup.h:242: error: template argument 4 is invalid
libs/glibmm2/glibmm/markup.h:266: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:266: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:267: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/markup.h:279: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:279: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:279: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/markup.h:292: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:292: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:292: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/markup.h:307: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:307: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:307: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/markup.h:353: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/markup.h:353: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/markup.h:353: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/markup.h:379: error: 'ustring' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/module.h:30: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/module.h:103: error: 'GModule' does not name a type
libs/glibmm2/glibmm/module.h:203: error: ISO C++ forbids declaration of 'GModule' with no type
libs/glibmm2/glibmm/module.h:203: error: expected ';' before '*' token
libs/glibmm2/glibmm/module.h:204: error: expected `;' before 'const'
libs/glibmm2/glibmm/module.h:204: error: ISO C++ forbids declaration of 'GModule' with no type
libs/glibmm2/glibmm/module.h:204: error: expected ';' before '*' token
libs/glibmm2/glibmm/module.h:206: error: expected `;' before 'protected'
libs/glibmm2/glibmm/module.h:207: error: ISO C++ forbids declaration of 'GModule' with no type
libs/glibmm2/glibmm/module.h:207: error: expected ';' before '*' token
libs/glibmm2/glibmm/optionentry.h:77: error: 'ustring' in namespace 'Glib' does not name a typelibs/glibmm2/glibmm/optionentry.h:78: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optionentry.h:78: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optionentry.h:78: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/optionentry.h:88: error: 'ustring' in namespace 'Glib' does not name a typelibs/glibmm2/glibmm/optionentry.h:89: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optionentry.h:89: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optionentry.h:89: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/optionentry.h:91: error: 'ustring' in namespace 'Glib' does not name a typelibs/glibmm2/glibmm/optionentry.h:92: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optionentry.h:92: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optionentry.h:92: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/optiongroup.h:61: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optiongroup.h:61: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optiongroup.h:61: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/optiongroup.h:79: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/optiongroup.h:79: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/optiongroup.h:79: error: template argument 1 is invalid
libs/glibmm2/glibmm/optiongroup.h:79: error: template argument 2 is invalid
libs/glibmm2/glibmm/optiongroup.h:84: error: 'Glib::ustring' has not been declared
libs/glibmm2/glibmm/optiongroup.h:84: error: 'void Glib::OptionGroup::add_entry(const Glib::OptionEntry&, int&)' cannot be overloaded
libs/glibmm2/glibmm/optiongroup.h:83: error: with 'void Glib::OptionGroup::add_entry(const Glib::OptionEntry&, int&)'
libs/glibmm2/glibmm/optiongroup.h:86: error: 'void Glib::OptionGroup::add_entry(const Glib::OptionEntry&, int&)' cannot be overloaded
libs/glibmm2/glibmm/optiongroup.h:83: error: with 'void Glib::OptionGroup::add_entry(const Glib::OptionEntry&, int&)'
libs/glibmm2/glibmm/optiongroup.h:102: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optiongroup.h:102: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optiongroup.h:102: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/optiongroup.h:128: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/optiongroup.h:128: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/optiongroup.h:128: error: template argument 1 is invalid
libs/glibmm2/glibmm/optiongroup.h:128: error: template argument 3 is invalid
libs/glibmm2/glibmm/optiongroup.h:128: error: template argument 4 is invalid
libs/glibmm2/glibmm/optioncontext.h:51: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optioncontext.h:51: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optioncontext.h:51: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/optioncontext.h:80: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/optioncontext.h:80: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/optioncontext.h:80: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/arrayhandle.h:85: error: 'OwnershipType' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/arrayhandle.h:102: error: 'OwnershipType' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/arrayhandle.h:125: error: 'OwnershipType' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/arrayhandle.h:205: error: 'Glib::OwnershipType' has not been declared
libs/glibmm2/glibmm/arrayhandle.h:206: error: 'Glib::OwnershipType' has not been declared
libs/glibmm2/glibmm/arrayhandle.h:233: error: 'OwnershipType' in namespace 'Glib' does not name a type
libs/glibmm2/glibmm/arrayhandle.h:243: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/arrayhandle.h:243: error: 'ustring' is not a member of 'Glib'
libs/glibmm2/glibmm/arrayhandle.h:243: error: template argument 1 is invalid
libs/glibmm2/glibmm/arrayhandle.h:243: error: template argument 2 is invalid
libs/glibmm2/glibmm/arrayhandle.h:243: error: invalid type in declaration before ';' token
libs/glibmm2/glibmm/arrayhandle.h: In constructor 'Glib::ArrayHandle<T, Tr>::ArrayHandle(const Cont&)':
libs/glibmm2/glibmm/arrayhandle.h:374: error: class 'Glib::ArrayHandle<T, Tr>' does not have any field named 'ownership_'
libs/glibmm2/glibmm/arrayhandle.h: At global scope:
libs/glibmm2/glibmm/arrayhandle.h:379: error: 'Glib::OwnershipType' has not been declared
libs/glibmm2/glibmm/arrayhandle.h: In constructor 'Glib::ArrayHandle<T, Tr>::ArrayHandle(const typename Tr::CType*, size_t, int)':
libs/glibmm2/glibmm/arrayhandle.h:383: error: class 'Glib::ArrayHandle<T, Tr>' does not have any field named 'ownership_'
libs/glibmm2/glibmm/arrayhandle.h: At global scope:
libs/glibmm2/glibmm/arrayhandle.h:388: error: 'Glib::OwnershipType' has not been declared
libs/glibmm2/glibmm/arrayhandle.h: In constructor 'Glib::ArrayHandle<T, Tr>::ArrayHandle(const typename Tr::CType*, int)':
libs/glibmm2/glibmm/arrayhandle.h:392: error: class 'Glib::ArrayHandle<T, Tr>' does not have any field named 'ownership_'
libs/glibmm2/glibmm/arrayhandle.h: In copy constructor 'Glib::ArrayHandle<T, Tr>::ArrayHandle(const Glib::ArrayHandle<T, Tr>&)':
libs/glibmm2/glibmm/arrayhandle.h:400: error: class 'Glib::ArrayHandle<T, Tr>' does not have any field named 'ownership_'
libs/glibmm2/glibmm/arrayhandle.h:402: error: 'OWNERSHIP_NONE' is not a member of 'Glib'
libs/glibmm2/glibmm/arrayhandle.h: In destructor 'Glib::ArrayHandle<T, Tr>::~ArrayHandle()':
libs/glibmm2/glibmm/arrayhandle.h:408: error: 'ownership_' was not declared in this scope
libs/glibmm2/glibmm/arrayhandle.h:408: error: 'OWNERSHIP_NONE' is not a member of 'Glib'
libs/glibmm2/glibmm/arrayhandle.h:410: error: 'OWNERSHIP_SHALLOW' is not a member of 'Glib'
libs/glibmm2/glibmm/arrayhandle.h: In member function 'Glib::ArrayHandle<T, Tr>::operator std::vector<U, std::allocator<_Tp1> >() const':
libs/glibmm2/glibmm/arrayhandle.h:443: error: 'fill_container' is not a member of 'Glib::Container_Helpers'
libs/glibmm2/glibmm/arrayhandle.h: In member function 'Glib::ArrayHandle<T, Tr>::operator std::deque<U, std::allocator<_Tp1> >() const':
libs/glibmm2/glibmm/arrayhandle.h:457: error: 'fill_container' is not a member of 'Glib::Container_Helpers'
libs/glibmm2/glibmm/arrayhandle.h: In member function 'Glib::ArrayHandle<T, Tr>::operator std::list<U, std::allocator<_Tp1> >() const':
libs/glibmm2/glibmm/arrayhandle.h:471: error: 'fill_container' is not a member of 'Glib::Container_Helpers'
libs/glibmm2/glibmm/arrayhandle.h: In member function 'void Glib::ArrayHandle<T, Tr>::assign_to(Cont&) const':
libs/glibmm2/glibmm/arrayhandle.h:485: error: 'fill_container' is not a member of 'Glib::Container_Helpers'
libs/glibmm2/glibmm/shell.h: At global scope:
libs/glibmm2/glibmm/shell.h:34: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/spawn.h:33: error: expected constructor, destructor, or type conversion before '(' token
libs/glibmm2/glibmm/thread.h:175: error: expected unqualified-id before '&' token
libs/glibmm2/glibmm/thread.h:175: error: expected ',' or '...' before '&' token
libs/glibmm2/glibmm/thread.h:175: error: ISO C++ forbids declaration of 'parameter' with no type
libs/glibmm2/glibmm/wrap_init.cc: In function 'void Glib::wrap_init()':
libs/glibmm2/glibmm/wrap_init.cc:57: error: 'Glib::FileError' has not been declared
libs/glibmm2/glibmm/wrap_init.cc:57: error: 'throw_func' was not declared in this scope
libs/glibmm2/glibmm/wrap_init.cc:61: error: 'Glib::ShellError' has not been declared
libs/glibmm2/glibmm/wrap_init.cc:62: error: 'Glib::SpawnError' has not been declared
scons: *** [libs/glibmm2/glibmm/wrap_init.os] Error 1
scons: building terminated because of errors.


---

### Post by MetalMusicAddict on 2006-05-31
Are there any screenshots of Ardour2?

---

### Post by dolson on 2006-05-31
The last I heard, Ardour2 wasn't even finished yet, but there have been Alpha releases.

Once, I had rebuilt packages from Debian for the Ardour2 Alpha1, and looks like they have Alpha2 there now:

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=ardour&searchon=names&subword=1&version=experimental&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=ardour&searchon=names&subword=1&version=experimental&release=all)

---

### Post by MetalMusicAddict on 2006-05-31
I did find [THIS]("http://taybin.com/node/31") but the link to the screenshot was broken.

---

### Post by hanzomon4 on 2006-05-31
Thanks for all the help

I installed gnome-common and some other stuff that stopped this intltool-update error I get.

But I still get all of the glibmm errors. I found the first error though but can't make any sense out of it 

> intltool-update -p -g=gtk_ardour
/usr/bin/xgettext: error while opening "../version.cc" for reading: No such file or directory
ERROR: xgettext failed to generate PO template file. Please consult
       error message above if there is any.


---

### Post by stbub on 2006-05-31
Try the following:

[http://taybin.com/gallery2/gallery/screenshots/ardour2.tiff.html?g2_imageViewsIndex=1](http://taybin.com/gallery2/gallery/screenshots/ardour2.tiff.html?g2_imageViewsIndex=1)

Although it's an audio app, so who cares about the look? :-)

---

### Post by hanzomon4 on 2006-05-31
[QUOTE=stbub]Try the following:

[http://taybin.com/gallery2/gallery/screenshots/ardour2.tiff.html?g2_imageViewsIndex=1](http://taybin.com/gallery2/gallery/screenshots/ardour2.tiff.html?g2_imageViewsIndex=1)

Although it's an audio app, so who cares about the look? :-)[/QUOTE]

Okay thank you, but I don't get it. That is a picture of the osx version of ardour2 and I'am trying to get the linux version of ardour2 to compile

_I get it now, my bad_

---

### Post by MetalMusicAddict on 2006-06-01
I just wanted to see because of the switch to GTK2. Im not sure if the screen is using it though it looks to be.

---

### Post by dolson on 2006-06-01
That is very much what it looks like under Linux. I won't bother actually using it until the 2.0 final is released and makes it into Debian. If this happens before Edgy's feature freeze, we will be requesting a Backport to Dapper, and I will do all I can to make that happen.

---

### Post by huwshimi on 2006-06-06
I just compiled Ardour 2 and it seems pretty good so far. A lot more polished than before. Good timing too, I have a big cd to finish.

---

### Post by MetalMusicAddict on 2006-06-06
[QUOTE=xi0nblue]I just compiled Ardour 2 and it seems pretty good so far. A lot more polished than before. Good timing too, I have a big cd to finish.[/QUOTE]
Not to keep harping about a screenshot but could you post one? Does it use your theme or is it black like the OSX one above? It would just be cool to see a Clearlooked or Ubuntulooked Ardour. :)

---

### Post by huwshimi on 2006-06-06
[IMG]http://huw.ugbox.net/stuff/ArdourScreenshot.png[/IMG]
As far as I know you can't theme it, but who knows? Maybe one day.

---

### Post by MetalMusicAddict on 2006-06-07
Thanx man that looks great. I wonder why it doesnt use your theme.:-k

Hows it runnin' for ya?

---

### Post by huwshimi on 2006-06-08
It had one crash but other that that it seems ok. I think that it uses the Wxwidgets libraries therefore not taking info from the Gtk theme (A bit of a guess really).

---

### Post by dolson on 2006-06-08
No, it is GTK2. That's all that Ardour2 is at the moment, it's just Ardour ported to GTK2.

---

### Post by huwshimi on 2006-06-08
Ok well I don't know why it's black then. Maybe one day it'll be themeable.

---

### Post by dolson on 2006-06-09
It's a good question. I hate the fact that it is not themable. I guess music apps are doomed to look like sh!t.

---

### Post by hanzomon4 on 2006-07-13
Finally  got it to work

---

### Post by huwshimi on 2006-07-14
> **dolson said:**
> It's a good question. I hate the fact that it is not themable. I guess music apps are doomed to look like sh!t.

It's is now themeable too.

---

### Post by zettberlin on 2006-07-14
Themes hmmmm... i dont know if any GTK-themes could be really usefull with Ardour. From the first time i had it running (in 2003 or so) i was impressed by the carefully custom-made graphics for sliders, buttons dialogues etc. Everything is made to fit with each other very well and i really do not believe, that the Desktop-orientaded graphs for GTK-themes could do so good for the very special tasks you need in a DAW.

In short: i am very very pleased with the graphs and the overall look of ardour - maybe it could be nice to manipulate the colors but i really cannot imagin, that anyone would love Ardours interface using the standardsliders as known from Gnome-mixer ;-)

---

### Post by dolson on 2006-07-14
zett, that's the only complaint I have, is the colors. It should pull the colors from the GTK theme. I wouldn't want to have Ardour skinnable, that would be silly indeed! But black?! Geez. :)

---

### Post by zettberlin on 2006-07-15
That is confirmed, dark fonts on a light grayish/blue background could improve the ardour-experience - esspecially when working whith it for 5-6 houres at nighttime in my bands basement ;-)
At least it would be good to have a chance trying it.

---

### Post by huwshimi on 2006-07-15
> **dolson said:**
> zett, that's the only complaint I have, is the colors. It should pull the colors from the GTK theme. I wouldn't want to have Ardour skinnable, that would be silly indeed! But black?! Geez. :)

If your remove the theme file it should revert to your GTK theme.

---

### Post by luneo on 2006-11-28
If someone needs Ardour2, Audacity 1.3.2, and some... just go to my site, i have made edgy packages... [http://luneo.zendurl.com]("http://luneo.zendurl.com")

---

### Post by uantuzri on 2007-03-01
> **luneo said:**
> If someone needs Ardour2, Audacity 1.3.2, and some... just go to my site, i have made edgy packages... [http://luneo.zendurl.com]("http://luneo.zendurl.com")

Hey that would solve all my problems while compiling... but your site is down. Is it a temporal closing or permanent?

Does anybody else knows where I can find the ardour2 packages?

---

### Post by eric71 on 2007-03-02
> **uantuzri said:**
> Hey that would solve all my problems while compiling... but your site is down. Is it a temporal closing or permanent?

Does anybody else knows where I can find the ardour2 packages?

See this thread at the Ardour forums:

[http://ardour.org/node/755](http://ardour.org/node/755)

---

### Post by uantuzri on 2007-03-02
Thanks! 

I accidentally found the treviño's repository, linked on the ardour forum, just before I read your post :D

---

### Post by bomanizer on 2007-03-12
I get errors with some XML parsing stuff, so... anyone?

```
scons: *** [libs/pbd/xml++.o] Error 1
scons: building terminated because of errors.
```

The whole error output is in the attachment.

cheers!

---

### Post by eric71 on 2007-03-21
I was downloading the .deb for the great Colombo drum kit for Hydrogen yesterday, when I saw that Musix already had a .deb for Ardour2 beta12 available.  It installed and is running fine on Feisty. The server is quite busy at times, I think.

[ftp://musix.ourproject.org/pub/musix/deb/](ftp://musix.ourproject.org/pub/musix/deb/)

---

