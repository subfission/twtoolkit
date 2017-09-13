# TWToolkit

This toolset leverages the Trustwave API for auditing and command line platform management.

### Features

  - Audit application list against Trustwave
  - Find broken URLs that impede the scanner
  - Discover CAS Authenticated URLs
  - Detect application existance
  - Detect deleted/misconfigured web applcations
  - Multithreaded for performance
  - Exportable to XLSX & CSV

## Usage

Both tools require a configuration file to be edited with your TrustWave account credentials.  This file will be automatically generated during the first run.

```
usage: twtoolkit [-h] [--quiet] [--debug] [--config CONFIG] {tamper|scrape|file}

This toolkit will check your Excel or CSV file for issues that can prevent a
scan from completing.

positional arguments:
  {tamper,scrape,file}  Switch between web-scrape mode, file analyser, and
                        tamper (interactive mode).
    tamper              Tamper mode for interactive editing.
    scrape              Activate the web scraping mode for quick web auditing.
    audit               Audit mode for inventory audit and reporting.

optional arguments:
  -h, --help            show this help message and exit
  --quiet, -q           Disable status messages and return only valid entries.
  --debug               Enable Debug mode (increases runtime duration).
  --config CONFIG       Select an alternative named configuration block.

```

### Supported File Mode File-Types:

  1. CSV (comma separated values).

     ** Requires that column[0] is the URLs and column[1] is the application names. Other fields are ignored.

  2. XLSX (Excel Spreadsheets)

     This will parse every sheet in workbook and does not have a known size restriction.

     **Requires a Column heading of "Title" and "URL" to be listed.  All other columns are ignored.

## Help

Each operation mode (tamper, file, scrape) has independent optional arguments including help menus.

Type `--help` or `-h` after the mode to view the respective options.

Example:
```
twtoolkit scrape --help

usage: twtoolkit scrape [-h] [--save {txt,xlsx}] [--quiet]
                        [--username USERNAME] [--password PASSWORD]

optional arguments:
  -h, --help            show this help message and exit
  --save {txt,xlsx}, -s {txt,xlsx}
                        Save output to text or spreadsheet file.
  --quiet, -q           Disable status messages and return only valid entries.
  --username USERNAME, -u USERNAME
                        Set the username as an argument for scripted queries.
  --password PASSWORD, -p PASSWORD
                        Set the login password and skip prompting for usage in
                        scripted queries.
```

### Installation

These tools have been compiled with python3.5.  Currently, the tools support:
 * MAC OS 10.7+

Your security settings may require you to sudo.
```sh
sudo chmod +x twtoolkit
sudo cp twtoolkit /usr/local/bin/
```
Finally, run the binary:
```sh
twtoolkit -h
```

## Roadmap ##
_Note: These are not arranged in any priority._
- Update assessment option for tinker
- Update an existing application
- Universally set application passwords for all applications under user
- Configure recurrence for assessments
- Clean up codebase
    - Convert all related processes to objects
    - Increase code comment coverage
- Full Trustwave API method coverage
- HTML output support
- Process daemonization / Headless mode
    - Web management & audit status option for localhost accounts
    - Logging & event auditing
- Windows 10 support
- Linux support
- Auto-create during audit mode


License
----

Written by Zach Jetson <zach.jetson@gmail.com>, December 2016

