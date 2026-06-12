---
title: "inkscape-0.46 fails to build with --with-python"
date: 2009-05-27
forum: Multimedia Software
---

### Post by jsteidl on 2009-05-27
i am having a problem recompiling inkscape-0.46 on ubuntu-9.04 on an x86 arch.

the reason i want to recompile is, that i want inkscape with script-support which is apparently disabled by default (why? i don't know ...) and can be enabled with the configure-option '--with-python'.

aaaaaanyways: there is a catch. when i use the default sources & ./debian/rules i can build it with 

```

apt-get source inkscape
apt-get build-dep inkscape
cd inkscape-0.46
debuild -us -uc
```

which puts a .deb in the parent-directory. easy.

when modifying the ./debian/rules (by adding a '--with-python \' to the configure-section i get a lot of file-not-found-errors which is kind of nasty.


```

	i486-linux-gnu-g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include/python2.6 -I/usr/include/freetype2  -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DRELAYTOOL_CRYPTO='static const int libcrypto_is_present = 1; static int __attribute__((unused)) libcrypto_symbol_is_present(char *m) { return 1; }' -DRELAYTOOL_SSL='static const int libssl_is_present = 1; static int __attribute__((unused)) libssl_symbol_is_present(char *m) { return 1; }'   -DHAVE_SSL -I/usr/include/libwpg-0.1 -I/usr/include/libwpd-0.8   -I/usr/include/freetype2   -I/usr/include/poppler   -D_REENTRANT -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -DPOTRACE=\"potrace\" -D_REENTRANT -pthread -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/atk-1.0 -I/usr/include/libxml2 -I/usr/include/gtkspell-2.0   -I../cxxtest    -Wall -g -O2   -MT extension/script/InkscapePython.o -MD -MP -MF $depbase.Tpo -c -o extension/script/InkscapePython.o extension/script/InkscapePython.cpp &&\
	mv -f $depbase.Tpo $depbase.Po
In Datei, eingefügt von extension/script/InkscapePython.cpp:19:
extension/script/CXX/Extensions.hxx:48:28: Fehler: CXX/WrapPython.h: No such file or directory
extension/script/CXX/Extensions.hxx:49:27: Fehler: CXX/Version.hxx: No such file or directory
extension/script/CXX/Extensions.hxx:50:26: Fehler: CXX/Config.hxx: No such file or directory
extension/script/CXX/Extensions.hxx:51:27: Fehler: CXX/Objects.hxx: No such file or directory
In Datei, eingefügt von extension/script/InkscapePython.cpp:20:
extension/script/CXX/Objects.hxx:44:29: Fehler: CXX/Exception.hxx: No such file or directory
extension/script/CXX/Objects.hxx:47:10: Fehler: #include erwartet "DATEINAME" oder <DATEINAME>
In file included from extension/script/InkscapePython.cpp:19:
extension/script/CXX/Extensions.hxx:67: Fehler: expected class-name before »{« token
extension/script/CXX/Extensions.hxx:112: Fehler: expected identifier before »*« token
extension/script/CXX/Extensions.hxx:112: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:112: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:112: Fehler: ISO-C++ verbietet Deklaration von »Tuple« ohne Typ
extension/script/CXX/Extensions.hxx:112: Fehler: »Object« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:113: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:113: Fehler: »method_keyword_function_t« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:113: Fehler: ISO-C++ verbietet Deklaration von »Tuple« ohne Typ
extension/script/CXX/Extensions.hxx:118: Fehler: »method_varargs_function_t« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:153: Fehler: »method_varargs_function_t« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx: In constructor »Py::MethodDefExt<T>::MethodDefExt(const char*, int, PyObject* (*)(PyObject*, PyObject*), const char*)«:
extension/script/CXX/Extensions.hxx:128: Fehler: »ext_varargs_function« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: In constructor »Py::MethodDefExt<T>::MethodDefExt(const char*, int (T::*)(int), PyObject* (*)(PyObject*, PyObject*, PyObject*), const char*)«:
extension/script/CXX/Extensions.hxx:145: Fehler: »ext_varargs_function« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: At global scope:
extension/script/CXX/Extensions.hxx:163: Fehler: »Module« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:164: Fehler: »Dict« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:166: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:167: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:195: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:206: Fehler: »T« is not a class or namespace
extension/script/CXX/Extensions.hxx:206: Fehler: expected identifier before »*« token
extension/script/CXX/Extensions.hxx:206: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:206: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:206: Fehler: ISO-C++ verbietet Deklaration von »Tuple« ohne Typ
extension/script/CXX/Extensions.hxx:206: Fehler: »Object« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:207: Fehler: »T« is not a class or namespace
extension/script/CXX/Extensions.hxx:207: Fehler: expected unqualified-id before »*« token
extension/script/CXX/Extensions.hxx:207: Fehler: expected `)' before »*« token
extension/script/CXX/Extensions.hxx:208: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:208: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:208: Fehler: Templateargument 2 ist ungültig
extension/script/CXX/Extensions.hxx:208: Fehler: Templateargument 4 ist ungültig
extension/script/CXX/Extensions.hxx:210: Fehler: »method_varargs_function_t« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:225: Fehler: »method_keyword_function_t« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:285: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:285: Fehler: »invoke_method_keyword« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:285: Fehler: ISO-C++ verbietet Deklaration von »Tuple« ohne Typ
extension/script/CXX/Extensions.hxx:303: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:303: Fehler: »invoke_method_varargs« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:303: Fehler: ISO-C++ verbietet Deklaration von »Tuple« ohne Typ
extension/script/CXX/Extensions.hxx: In static member function »static void Py::ExtensionModule<T>::add_varargs_method(const char*, int, const char*)«:
extension/script/CXX/Extensions.hxx:214: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:214: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:214: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:214: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:214: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:220: Fehler: new initializer Ausdrucksliste als zusammengesetzten Ausdruck behandelt
extension/script/CXX/Extensions.hxx:220: Warnung: right-hand operand of comma ist eine Referenz, kein Aufruf, zur Funktion »Py::method_varargs_call_handler«
extension/script/CXX/Extensions.hxx:222: Fehler: no match für »operator[]« in »mm[(std::string)(name)]«
extension/script/CXX/Extensions.hxx: In static member function »static void Py::ExtensionModule<T>::add_keyword_method(const char*, int, const char*)«:
extension/script/CXX/Extensions.hxx:229: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:229: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:229: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:229: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:229: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:235: Fehler: new initializer Ausdrucksliste als zusammengesetzten Ausdruck behandelt
extension/script/CXX/Extensions.hxx:235: Warnung: right-hand operand of comma ist eine Referenz, kein Aufruf, zur Funktion »Py::method_keyword_call_handler«
extension/script/CXX/Extensions.hxx:237: Fehler: no match für »operator[]« in »mm[(std::string)(name)]«
extension/script/CXX/Extensions.hxx: In member function »void Py::ExtensionModule<T>::initialize(const char*)«:
extension/script/CXX/Extensions.hxx:243: Fehler: »Dict« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:243: Fehler: expected `;' before »dict«
extension/script/CXX/Extensions.hxx:250: Fehler: »EXPLICIT_TYPENAME« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:250: Fehler: expected `;' before »method_map_t«
extension/script/CXX/Extensions.hxx:252: Fehler: »i« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:252: Fehler: Abfrage des Elementes »begin« in »mm«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:252: Fehler: Abfrage des Elementes »end« in »mm«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:254: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:254: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:254: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:258: Fehler: »Tuple« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:258: Fehler: expected `;' before »args«
extension/script/CXX/Extensions.hxx:259: Fehler: »args« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:260: Fehler: es gibt keine Argumente für »String«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »String« verfügbar sein muss
extension/script/CXX/Extensions.hxx:260: Fehler: (mit »-fpermissive« wird G++ den Code akzeptieren, aber die Verwendung eines nicht deklarierten Namens ist veraltet)
extension/script/CXX/Extensions.hxx:262: Fehler: Abfrage des Elementes »ext_meth_def« in »method_definition->«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:262: Fehler: es gibt keine Argumente für »new_reference_to«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »new_reference_to« verfügbar sein muss
extension/script/CXX/Extensions.hxx:268: Fehler: »dict« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: In member function »virtual int Py::ExtensionModule<T>::invoke_method_keyword(const std::string&, int)«:
extension/script/CXX/Extensions.hxx:288: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:288: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:288: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:288: Fehler: no match für »operator[]« in »mm[name]«
extension/script/CXX/Extensions.hxx:293: Fehler: es gibt keine Argumente für »RuntimeError«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »RuntimeError« verfügbar sein muss
extension/script/CXX/Extensions.hxx:297: Fehler: »self« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:297: Fehler: expected type-specifier before »T«
extension/script/CXX/Extensions.hxx:297: Fehler: expected `>' before »T«
extension/script/CXX/Extensions.hxx:297: Fehler: expected `(' before »T«
extension/script/CXX/Extensions.hxx:297: Fehler: expected primary-expression before »>« token
extension/script/CXX/Extensions.hxx:297: Fehler: expected `)' before »;« token
extension/script/CXX/Extensions.hxx:299: Fehler: Abfrage des Elementes »ext_keyword_function« in »meth_def->«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:299: Fehler: »args« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:299: Fehler: »keywords« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: In member function »virtual int Py::ExtensionModule<T>::invoke_method_varargs(const std::string&, int)«:
extension/script/CXX/Extensions.hxx:306: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:306: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:306: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:306: Fehler: no match für »operator[]« in »mm[name]«
extension/script/CXX/Extensions.hxx:311: Fehler: es gibt keine Argumente für »RuntimeError«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »RuntimeError« verfügbar sein muss
extension/script/CXX/Extensions.hxx:315: Fehler: »self« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:315: Fehler: expected type-specifier before »T«
extension/script/CXX/Extensions.hxx:315: Fehler: expected `>' before »T«
extension/script/CXX/Extensions.hxx:315: Fehler: expected `(' before »T«
extension/script/CXX/Extensions.hxx:315: Fehler: expected primary-expression before »>« token
extension/script/CXX/Extensions.hxx:315: Fehler: expected `)' before »;« token
extension/script/CXX/Extensions.hxx:317: Fehler: Abfrage des Elementes »ext_varargs_function« in »meth_def->«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:317: Fehler: »args« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: At global scope:
extension/script/CXX/Extensions.hxx:414: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:415: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:415: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:416: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:417: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:417: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:418: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:418: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:419: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:420: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:422: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:423: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:428: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:429: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:430: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:431: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:432: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:432: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:433: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:433: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:437: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:438: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:438: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:442: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:443: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:444: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:445: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:446: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:447: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:448: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:449: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:450: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:451: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:452: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:453: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:454: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:455: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:456: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:457: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:458: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:459: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:460: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:461: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:462: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:474: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:489: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:489: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:499: Fehler: »Object« bezeichnet keinen Typ
extension/script/CXX/Extensions.hxx:540: Fehler: »T« is not a class or namespace
extension/script/CXX/Extensions.hxx:540: Fehler: expected identifier before »*« token
extension/script/CXX/Extensions.hxx:540: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:540: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:540: Fehler: ISO-C++ verbietet Deklaration von »Tuple« ohne Typ
extension/script/CXX/Extensions.hxx:540: Fehler: »Object« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:541: Fehler: »T« is not a class or namespace
extension/script/CXX/Extensions.hxx:541: Fehler: expected unqualified-id before »*« token
extension/script/CXX/Extensions.hxx:541: Fehler: expected `)' before »*« token
extension/script/CXX/Extensions.hxx:542: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:542: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:542: Fehler: Templateargument 2 ist ungültig
extension/script/CXX/Extensions.hxx:542: Fehler: Templateargument 4 ist ungültig
extension/script/CXX/Extensions.hxx:545: Fehler: »getattr_default« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:576: Fehler: »getattr_methods« als Funktion, die eine Funktion zurückgibt, deklariert
extension/script/CXX/Extensions.hxx:608: Fehler: »method_varargs_function_t« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:623: Fehler: »method_keyword_function_t« wurde nicht deklariert
extension/script/CXX/Extensions.hxx: In static member function »static int Py::PythonExtension<T>::check(int)«:
extension/script/CXX/Extensions.hxx:491: Fehler: »ob« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: In member function »virtual int Py::PythonExtension<T>::getattr_default(const char*)«:
extension/script/CXX/Extensions.hxx:551: Fehler: »String« ist kein Element von »Py«
extension/script/CXX/Extensions.hxx:555: Fehler: »String« ist kein Element von »Py«
extension/script/CXX/Extensions.hxx: In member function »virtual int Py::PythonExtension<T>::getattr_methods(const char*)«:
extension/script/CXX/Extensions.hxx:584: Fehler: »List« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:584: Fehler: expected `;' before »methods«
extension/script/CXX/Extensions.hxx:586: Fehler: »EXPLICIT_TYPENAME« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:586: Fehler: expected `;' before »method_map_t«
extension/script/CXX/Extensions.hxx:586: Fehler: »i« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:586: Fehler: Abfrage des Elementes »end« in »mm«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:587: Fehler: es gibt keine Argumente für »String«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »String« verfügbar sein muss
extension/script/CXX/Extensions.hxx:593: Fehler: Abfrage des Elementes »find« in »mm«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:593: Fehler: Abfrage des Elementes »end« in »mm«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:594: Fehler: es gibt keine Argumente für »AttributeError«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »AttributeError« verfügbar sein muss
extension/script/CXX/Extensions.hxx:596: Fehler: »Tuple« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:596: Fehler: expected `;' before »self«
extension/script/CXX/Extensions.hxx:598: Fehler: »self« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:599: Fehler: es gibt keine Argumente für »String«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »String« verfügbar sein muss
extension/script/CXX/Extensions.hxx:601: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:601: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:601: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:601: Fehler: no match für »operator[]« in »mm[name]«
extension/script/CXX/Extensions.hxx:603: Fehler: Abfrage des Elementes »ext_meth_def« in »method_definition->«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx: In static member function »static void Py::PythonExtension<T>::add_varargs_method(const char*, int, const char*)«:
extension/script/CXX/Extensions.hxx:612: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:612: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:612: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:612: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:612: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:620: Fehler: no match für »operator[]« in »mm[(std::string)(name)]«
extension/script/CXX/Extensions.hxx: In static member function »static void Py::PythonExtension<T>::add_keyword_method(const char*, int, const char*)«:
extension/script/CXX/Extensions.hxx:627: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:627: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:627: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:627: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:627: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:635: Fehler: no match für »operator[]« in »mm[(std::string)(name)]«
extension/script/CXX/Extensions.hxx: In static member function »static PyObject* Py::PythonExtension<T>::method_keyword_call_handler(PyObject*, PyObject*, PyObject*)«:
extension/script/CXX/Extensions.hxx:652: Fehler: »Tuple« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:652: Fehler: expected `;' before »self_and_name_tuple«
extension/script/CXX/Extensions.hxx:654: Fehler: »self_and_name_tuple« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:655: Fehler: »self« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:655: Fehler: expected type-specifier before »T«
extension/script/CXX/Extensions.hxx:655: Fehler: expected `>' before »T«
extension/script/CXX/Extensions.hxx:655: Fehler: expected `(' before »T«
extension/script/CXX/Extensions.hxx:655: Fehler: expected primary-expression before »>« token
extension/script/CXX/Extensions.hxx:655: Fehler: expected `)' before »;« token
extension/script/CXX/Extensions.hxx:657: Fehler: »String« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:657: Fehler: expected `;' before »name«
extension/script/CXX/Extensions.hxx:660: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:660: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:660: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:660: Fehler: »name« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:664: Fehler: expected `;' before »args«
extension/script/CXX/Extensions.hxx:667: Fehler: »Dict« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:667: Fehler: expected `;' before »keywords«
extension/script/CXX/Extensions.hxx:669: Fehler: »keywords« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:671: Fehler: Funktion »int Py::result(int*)« ist wie eine Variable initialisiert
extension/script/CXX/Extensions.hxx:671: Fehler: Abfrage des Elementes »ext_keyword_function« in »meth_def->«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:671: Fehler: »args« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:671: Fehler: »keywords« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:673: Fehler: »result« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:673: Fehler: es gibt keine Argumente für »new_reference_to«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »new_reference_to« verfügbar sein muss
extension/script/CXX/Extensions.hxx:675: Fehler: expected type-specifier before »Exception«
extension/script/CXX/Extensions.hxx:675: Fehler: expected `)' before »&« token
extension/script/CXX/Extensions.hxx:675: Fehler: expected `{' before »&« token
extension/script/CXX/Extensions.hxx:675: Fehler: expected primary-expression before »)« token
extension/script/CXX/Extensions.hxx:675: Fehler: expected `;' before »)« token
extension/script/CXX/Extensions.hxx: In static member function »static PyObject* Py::PythonExtension<T>::method_varargs_call_handler(PyObject*, PyObject*)«:
extension/script/CXX/Extensions.hxx:685: Fehler: »Tuple« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:685: Fehler: expected `;' before »self_and_name_tuple«
extension/script/CXX/Extensions.hxx:687: Fehler: »self_and_name_tuple« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:688: Fehler: »self« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:688: Fehler: expected type-specifier before »T«
extension/script/CXX/Extensions.hxx:688: Fehler: expected `>' before »T«
extension/script/CXX/Extensions.hxx:688: Fehler: expected `(' before »T«
extension/script/CXX/Extensions.hxx:688: Fehler: expected primary-expression before »>« token
extension/script/CXX/Extensions.hxx:688: Fehler: expected `)' before »;« token
extension/script/CXX/Extensions.hxx:690: Fehler: »String« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:690: Fehler: expected `;' before »name«
extension/script/CXX/Extensions.hxx:693: Fehler: Typ/Wert des Arguments 1 passt nicht in Template-Parameterliste für »template<class T> class Py::MethodDefExt«
extension/script/CXX/Extensions.hxx:693: Fehler:   einen Typ erwartet, »T« erhalten
extension/script/CXX/Extensions.hxx:693: Fehler: invalid type in declaration before »=« token
extension/script/CXX/Extensions.hxx:693: Fehler: »name« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:697: Fehler: expected `;' before »args«
extension/script/CXX/Extensions.hxx:713: Fehler: Abfrage des Elementes »ext_varargs_function« in »meth_def->«, das vom Nicht-Klassentyp »int« ist
extension/script/CXX/Extensions.hxx:713: Fehler: »args« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:718: Fehler: expected type-specifier before »Exception«
extension/script/CXX/Extensions.hxx:718: Fehler: expected `)' before »&« token
extension/script/CXX/Extensions.hxx:718: Fehler: expected `{' before »&« token
extension/script/CXX/Extensions.hxx:718: Fehler: expected primary-expression before »)« token
extension/script/CXX/Extensions.hxx:718: Fehler: expected `;' before »)« token
extension/script/CXX/Extensions.hxx: In static member function »static void Py::PythonExtension<T>::extension_object_deallocator(PyObject*)«:
extension/script/CXX/Extensions.hxx:726: Fehler: expected primary-expression before »)« token
extension/script/CXX/Extensions.hxx: At global scope:
extension/script/CXX/Extensions.hxx:739: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Extensions.hxx:741: Fehler: expected class-name before »{« token
extension/script/CXX/Extensions.hxx:756: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:756: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:762: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Extensions.hxx:762: Fehler: ISO-C++ verbietet Deklaration von »Object« ohne Typ
extension/script/CXX/Extensions.hxx:783: Fehler: ISO-C++ verbietet Deklaration von »T« ohne Typ
extension/script/CXX/Extensions.hxx:783: Fehler: expected »;« before »*« token
extension/script/CXX/Extensions.hxx:787: Fehler: expected `;' before »}« token
extension/script/CXX/Extensions.hxx: In constructor »Py::ExtensionObject<T>::ExtensionObject(PyObject*)«:
extension/script/CXX/Extensions.hxx:745: Fehler: Klasse »Py::ExtensionObject<T>« hat keinen Feldnamen »Object«
extension/script/CXX/Extensions.hxx:747: Fehler: es gibt keine Argumente für »validate«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »validate« verfügbar sein muss
extension/script/CXX/Extensions.hxx: In copy constructor »Py::ExtensionObject<T>::ExtensionObject(const Py::ExtensionObject<T>&)«:
extension/script/CXX/Extensions.hxx:751: Fehler: Klasse »Py::ExtensionObject<T>« hat keinen Feldnamen »Object«
extension/script/CXX/Extensions.hxx:753: Fehler: es gibt keine Argumente für »validate«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »validate« verfügbar sein muss
extension/script/CXX/Extensions.hxx: In constructor »Py::ExtensionObject<T>::ExtensionObject(int)«:
extension/script/CXX/Extensions.hxx:757: Fehler: Klasse »Py::ExtensionObject<T>« hat keinen Feldnamen »Object«
extension/script/CXX/Extensions.hxx:757: Fehler: »other« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx:759: Fehler: es gibt keine Argumente für »validate«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »validate« verfügbar sein muss
extension/script/CXX/Extensions.hxx: In member function »Py::ExtensionObject<T>& Py::ExtensionObject<T>::operator=(int)«:
extension/script/CXX/Extensions.hxx:764: Fehler: »rhs« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Extensions.hxx: In member function »Py::ExtensionObject<T>& Py::ExtensionObject<T>::operator=(PyObject*)«:
extension/script/CXX/Extensions.hxx:769: Fehler: es gibt keine Argumente für »ptr«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »ptr« verfügbar sein muss
extension/script/CXX/Extensions.hxx:771: Fehler: es gibt keine Argumente für »set«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »set« verfügbar sein muss
extension/script/CXX/Extensions.hxx: In member function »virtual bool Py::ExtensionObject<T>::accepts(PyObject*) const«:
extension/script/CXX/Extensions.hxx:777: Fehler: »T« is not a class or namespace
In file included from extension/script/InkscapePython.cpp:20:
extension/script/CXX/Objects.hxx: At global scope:
extension/script/CXX/Objects.hxx:60: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Objects.hxx:63: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Objects.hxx: In function »PyObject* Py::new_reference_to(PyObject*)«:
extension/script/CXX/Objects.hxx:68: Fehler: »_XINCREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: At global scope:
extension/script/CXX/Objects.hxx:194: Fehler: »_None« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »void Py::Object::set(PyObject*, bool)«:
extension/script/CXX/Objects.hxx:160: Fehler: »_XINCREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »void Py::Object::release()«:
extension/script/CXX/Objects.hxx:167: Fehler: »_XDECREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »void Py::Object::validate()«:
extension/script/CXX/Objects.hxx:179: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx:185: Fehler: »TypeError« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In constructor »Py::Object::Object(PyObject*, bool)«:
extension/script/CXX/Objects.hxx:198: Fehler: »_XINCREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In copy constructor »Py::Object::Object(const Py::Object&)«:
extension/script/CXX/Objects.hxx:206: Fehler: »_XINCREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »void Py::Object::increment_reference_count()«:
extension/script/CXX/Objects.hxx:239: Fehler: »_XINCREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »void Py::Object::decrement_reference_count()«:
extension/script/CXX/Objects.hxx:246: Fehler: »RuntimeError« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx:247: Fehler: »_XDECREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::isDict() const«:
extension/script/CXX/Objects.hxx:333: Fehler: »_Dict_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::isList() const«:
extension/script/CXX/Objects.hxx:338: Fehler: »_List_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::isTuple() const«:
extension/script/CXX/Objects.hxx:365: Fehler: »_Tuple_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::isString() const«:
extension/script/CXX/Objects.hxx:370: Fehler: »_String_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx:370: Fehler: »_Unicode_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::isUnicode() const«:
extension/script/CXX/Objects.hxx:375: Fehler: »_Unicode_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »void Py::Object::setAttr(const std::string&, const Py::Object&)«:
extension/script/CXX/Objects.hxx:382: Fehler: »AttributeError« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »void Py::Object::delAttr(const std::string&)«:
extension/script/CXX/Objects.hxx:388: Fehler: »AttributeError« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »void Py::Object::delItem(const Py::Object&)«:
extension/script/CXX/Objects.hxx:398: Fehler: »KeyError« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::operator==(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:405: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::operator!=(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:412: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::operator>=(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:420: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::operator<=(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:427: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::operator<(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:434: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::Object::operator>(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:441: Fehler: »Exception« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In function »PyObject* Py::new_reference_to(const Py::Object&)«:
extension/script/CXX/Objects.hxx:449: Fehler: »_XINCREF« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In function »Py::Object Py::Nothing()«:
extension/script/CXX/Objects.hxx:457: Fehler: »_None« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In function »Py::Object Py::None()«:
extension/script/CXX/Objects.hxx:463: Fehler: »_None« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »virtual bool Py::Type::accepts(PyObject*) const«:
extension/script/CXX/Objects.hxx:503: Fehler: »_Type_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »virtual bool Py::Int::accepts(PyObject*) const«:
extension/script/CXX/Objects.hxx:593: Fehler: »_Int_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »virtual bool Py::Long::accepts(PyObject*) const«:
extension/script/CXX/Objects.hxx:703: Fehler: »_Long_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »virtual bool Py::LongLong::accepts(PyObject*) const«:
extension/script/CXX/Objects.hxx:809: Fehler: »_Long_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »virtual bool Py::Float::accepts(PyObject*) const«:
extension/script/CXX/Objects.hxx:913: Fehler: »_Float_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: In member function »virtual bool Py::Complex::accepts(PyObject*) const«:
extension/script/CXX/Objects.hxx:983: Fehler: »_Complex_Check« ist kein Element von »Py«
extension/script/CXX/Objects.hxx: At global scope:
extension/script/CXX/Objects.hxx:1054: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Objects.hxx:1060: Fehler: »T« bezeichnet keinen Typ
extension/script/CXX/Objects.hxx:1080: Fehler: expected type-specifier before »T«
extension/script/CXX/Objects.hxx:1092: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Objects.hxx:1092: Fehler: ISO-C++ verbietet Deklaration von »T« ohne Typ
extension/script/CXX/Objects.hxx: In constructor »Py::seqref<T>::seqref(Py::SeqBase<T>&, Py::sequence_index_type)«:
extension/script/CXX/Objects.hxx:1064: Fehler: Klasse »Py::seqref<T>« hat keinen Feldnamen »the_item«
extension/script/CXX/Objects.hxx: In copy constructor »Py::seqref<T>::seqref(const Py::seqref<T>&)«:
extension/script/CXX/Objects.hxx:1068: Fehler: Klasse »Py::seqref<T>« hat keinen Feldnamen »the_item«
extension/script/CXX/Objects.hxx: In constructor »Py::seqref<T>::seqref(Py::Object&)«:
extension/script/CXX/Objects.hxx:1075: Fehler: Klasse »Py::seqref<T>« hat keinen Feldnamen »the_item«
extension/script/CXX/Objects.hxx: In member function »Py::seqref<T>& Py::seqref<T>::operator=(const Py::seqref<T>&)«:
extension/script/CXX/Objects.hxx:1087: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »Py::seqref<T>& Py::seqref<T>::operator=(int)«:
extension/script/CXX/Objects.hxx:1092: Fehler: Deklaration von »const int T«
extension/script/CXX/Objects.hxx:1054: Fehler:  überdeckt Templateparameter »int T«
extension/script/CXX/Objects.hxx:1094: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx:1094: Fehler: »ob« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »PyObject* Py::seqref<T>::ptr() const«:
extension/script/CXX/Objects.hxx:1102: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »int Py::seqref<T>::reference_count() const«:
extension/script/CXX/Objects.hxx:1107: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »Py::Type Py::seqref<T>::type() const«:
extension/script/CXX/Objects.hxx:1112: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::hasAttr(const std::string&) const«:
extension/script/CXX/Objects.hxx:1121: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »Py::Object Py::seqref<T>::getAttr(const std::string&) const«:
extension/script/CXX/Objects.hxx:1126: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »Py::Object Py::seqref<T>::getItem(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1131: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »long int Py::seqref<T>::hashValue() const«:
extension/script/CXX/Objects.hxx:1136: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isCallable() const«:
extension/script/CXX/Objects.hxx:1141: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isInstance() const«:
extension/script/CXX/Objects.hxx:1146: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isDict() const«:
extension/script/CXX/Objects.hxx:1151: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isList() const«:
extension/script/CXX/Objects.hxx:1156: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isMapping() const«:
extension/script/CXX/Objects.hxx:1161: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isNumeric() const«:
extension/script/CXX/Objects.hxx:1166: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isSequence() const«:
extension/script/CXX/Objects.hxx:1171: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isTrue() const«:
extension/script/CXX/Objects.hxx:1176: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isType(const Py::Type&) const«:
extension/script/CXX/Objects.hxx:1181: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isTuple() const«:
extension/script/CXX/Objects.hxx:1186: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::isString() const«:
extension/script/CXX/Objects.hxx:1191: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »void Py::seqref<T>::setAttr(const std::string&, const Py::Object&)«:
extension/script/CXX/Objects.hxx:1196: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »void Py::seqref<T>::delAttr(const std::string&)«:
extension/script/CXX/Objects.hxx:1201: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »void Py::seqref<T>::delItem(const Py::Object&)«:
extension/script/CXX/Objects.hxx:1206: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::operator==(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1211: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::operator!=(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1216: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::operator>=(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1221: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::operator<=(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1226: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::operator<(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1231: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: In member function »bool Py::seqref<T>::operator>(const Py::Object&) const«:
extension/script/CXX/Objects.hxx:1236: Fehler: »the_item« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx: At global scope:
extension/script/CXX/Objects.hxx:1244: Fehler: »TEMPLATE_TYPENAME« wurde nicht deklariert
extension/script/CXX/Objects.hxx:1251: Fehler: »T« bezeichnet keinen Typ
extension/script/CXX/Objects.hxx:1254: Fehler: »T« bezeichnet keinen Typ
extension/script/CXX/Objects.hxx:1320: Fehler: ISO-C++ verbietet Deklaration von »T« ohne Typ
extension/script/CXX/Objects.hxx:1320: Fehler: expected »;« before »operator«
extension/script/CXX/Objects.hxx:1325: Fehler: expected `;' before »seqref«
extension/script/CXX/Objects.hxx:1330: Fehler: »T« bezeichnet keinen Typ
extension/script/CXX/Objects.hxx:1335: Fehler: expected »,« or »...« before »&« token
extension/script/CXX/Objects.hxx:1335: Fehler: ISO-C++ verbietet Deklaration von »T« ohne Typ
extension/script/CXX/Objects.hxx:1354: Fehler: »T« bezeichnet keinen Typ
extension/script/CXX/Objects.hxx:1364: Fehler: »T« bezeichnet keinen Typ
extension/script/CXX/Objects.hxx:1388: Fehler: expected class-name before »(« token
extension/script/CXX/Objects.hxx:1388: Fehler: expected `{' before »(« token
extension/script/CXX/Objects.hxx:1388: Fehler: invalid declarator before »)« token
extension/script/InkscapePython.cpp:498: Fehler: expected `}' at end of input
extension/script/CXX/Objects.hxx: In member function »virtual void Py::SeqBase<T>::setItem(Py::sequence_index_type, int)«:
extension/script/CXX/Objects.hxx:1335: Fehler: Deklaration von »const int T«
extension/script/CXX/Objects.hxx:1244: Fehler:  überdeckt Templateparameter »int T«
extension/script/CXX/Objects.hxx:1337: Fehler: »ob« wurde in diesem Gültigkeitsbereich nicht definiert
extension/script/CXX/Objects.hxx:1339: Fehler: es gibt keine Argumente für »Exception«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »Exception« verfügbar sein muss
extension/script/CXX/Objects.hxx: In member function »void Py::SeqBase<T>::verify_length(size_t) const«:
extension/script/CXX/Objects.hxx:1377: Fehler: es gibt keine Argumente für »IndexError«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »IndexError« verfügbar sein muss
extension/script/CXX/Objects.hxx: In member function »void Py::SeqBase<T>::verify_length(size_t, size_t) const«:
extension/script/CXX/Objects.hxx:1384: Fehler: es gibt keine Argumente für »IndexError«, die von einem Templateparameter abhängen, weshalb eine Deklaration von »IndexError« verfügbar sein muss
extension/script/CXX/Objects.hxx: At global scope:
extension/script/CXX/Objects.hxx:1385: Fehler: expected unqualified-id at end of input
extension/script/CXX/Objects.hxx:1385: Fehler: expected `}' at end of input
make[3]: *** [extension/script/InkscapePython.o] Fehler 1
make[3]: Verlasse Verzeichnis '/home/jsteidl/inkscape-0.46/src'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/jsteidl/inkscape-0.46'
make[1]: *** [all] Fehler 2
make[1]: Verlasse Verzeichnis '/home/jsteidl/inkscape-0.46'
make: *** [build] Fehler 2
dpkg-buildpackage: Fehlschlag: debian/rules build gab Fehler-Exitstatus 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

is the source-code stripped to the files required by the default-build-set of debian? is there something i don't get here?

there is a tasty reward involved::popcorn: BUT YOU DON'T GET TO TOUCH IT UNTIL I CAN BUILD IT RIGHT!:evil:

---

