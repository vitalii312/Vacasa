Django-Select2
==============

This is a [Django](https://www.djangoproject.com/) integration of [Select2](http://ivaynberg.github.com/select2/).

The app includes Select2 driven Django Widgets and Form Fields.

Installation
============

1. Install `django_select2`

        pip install django_select2

2. Add `django_select2` to your `INSTALLED_APPS` in your project settings.

3. When deploying on production server, run :-

        python manage.py collectstatic

Documentation
=============

Documentation available at http://django-select2.readthedocs.org/.

More details
============

More details can be found on my blog at - http://blog.applegrew.com/2012/08/django-select2/.

External Dependencies
=====================

* Django - This is obvious.
* jQuery - This is not included in the package since it is expected that in most scenarios this would already be available.

Example Application
===================
Please see `testapp` application. This application is used to manually test the functionalities of this package. This also serves as a good example.

You need only Django 1.4 or above to run that. It might run on older versions but that is not tested.

Special Thanks
==============

* Samuel Goldszmidt (@ouhouhsami) for reporting many fundamental issues with the code, because of which versions 2.0 and 2.0.1 were released.

Changelog Summary
=================

### v3.1.2

* Fixed issue#7.

### v3.1.1

* Bumping up minor version since Select2 JS has been updated to version 3.2. It seems Select2 JS now includes new higher resolution icons for [Retina displays](http://en.wikipedia.org/wiki/Retina_Display).
* Fixed an issue in `setup.py` because of which `templatetags` directory was not included in last PIP releases' tar file.

### v3.0.2

* Added `AUTO_RENDER_SELECT2_STATICS` settings. This, when specified and set to `False` in `settings.py` then Django_Select2 widgets won't automatically include the required scripts and stylesheets. When this setting is `True` (default) then every Select2 field on the page will output `<script>` and `<link>` tags to include the required JS and CSS files. This is convinient but will output the same JS and CSS files multiple times if there are more than one Select2 fields on the page.
* Added `django_select2_tags` template tags to manually include the required JS and CSS files, when `AUTO_RENDER_SELECT2_STATICS` is turned off.

### v3.0.1

* Revised the design of heavy fields. The previous design didn't quite make it easy to back heavy fields by big data sources. See `fields.HeavyChoiceField` class and its methods' docs for more info.
* Updated docs.
* Some more fixes for issue#4.
* Updated Select2 JS to version 3.1.

### v3.0

* Added docs.
* Some bug fixes. See issue#4.
* `widgets.Select2Mixin.__init__` now accepts `select2_options` kwarg to override its `options` settings. Previously `attrs` were being used for this too. This means backward compatibility has been broken here. `attrs` will no longer override `options` values. **The major release version has been changed to 3, because of this backward incompatible change.**

### v2.0.1

* Auto id registration fixes.

### v2.0

* Mostly major bug fixes in code and design. The changes were many, raising the possibility of backward incompatibility. However, the backward incompatibility would be subtle.

* Auto fields (sub-classes of AutoViewFieldMixin) now accepts `auto_id` parameter. This can be used to provide custom id for the field. The default is 'module.field_class_name'. Ideally only the first instance of an auto field is registered. This parameter can be used to force registration of additional instances by passing a unique value.
