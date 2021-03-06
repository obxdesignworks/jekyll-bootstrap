---
layout: post
categories : usage
---


## Switching Themes

Jekyll-bootstrap-core comes with two themes

- **tom** from [http://tom.preston-werner.com](http://tom.preston-werner.com)
- **mark-reid** from [http://mark.reid.name](http://mark.reid.name)

Switch themes via the rake task

    $ rake switch_theme['mark-reid']

If you are new to `rake` a rake task is just a ruby method that can be run in the base-directory
of jekyll-bootstrap-core. Feel free to view the [Rakefile](https://github.com/plusjade/jekyll-bootstrap-core/blob/master/Rakefile) source.

## Editing Themes

Theme layouts are contained in `./_includes/themes/THEME-NAME`.
It is important that you edit files in the theme directory rather than `_layouts` 
because switching themes will overwrite files in the `_layout` directory and you will lose your changes.
The main point here is keeping themes modular; this way editing one does not affect the other.

### Adding Templates

You are free add extra template files to `_layouts` in order to customize your blog.

However if you want to add theme-specific layouts you should add them to the theme's directory in `_includes`.
After your files are added make sure to run the switcher again:

    $ rake switch_theme['mark-reid']


### Static Assets

Static assets are name-spaced for each theme. They are available at `./assets/themes/THEME-NAME`.
Make sure you edit and add assets in this directory.
All themes are provided with the liquid variable: `theme_asset_path` which trace back to the aforementioned directory.

## Add Your Own Theme

To add your own theme just copy the theme structure of a current theme and change out the templates and assets.

At this time a theme needs two main but separate directory components:

1. **./\_includes/themes/THEME-NAME**  
  Any template defined in this folder will be usable as a normal layout once you run `rake switch_theme['THEME-NAME']`.
1. **./assets/themes/THEME-NAME**  
  Static assets for your theme should be namespaced via this folder.
  Your templates should use the liquid variable : `theme_asset_path` to call these assets.

