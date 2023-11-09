# i18next-json-to-csv

Converts i18next format JSON files to CSV (to be imported to Excel) and back.

## Install

```sh
$ npm i -g i18next-json-to-csv
```

Or with Yarn:

```sh
$ yarn global add i18next-json-to-csv
```

## CLI

### Convert JSON to CSV

```sh
$ i18next-json-to-csv ./en.json ./en.csv
```

### Convert CSV to JSON

**Requirements:** Encoding must be UTF-8, separator must be comma ( , ) lines must be separated by line breaks and all fields must be quoted.

```sh
$ i18next-json-to-csv ./en.csv ./en.json
```

*Note: As of this writing, Excel can't export a proper CSV for this (UTF-8 issues). LibreOffice Calc can.*

### Diff two CSV files

```sh
$ i18next-json-to-csv ./en-old.csv ./en-new.csv ./en-diff.csv
```

### Diff two CSV files and put the original labels in an extra column

```sh
$ i18next-json-to-csv ./en-old.csv ./en-new.csv ./en-diff.csv ./hu-HU-new.csv
```

## API

### json2Csv(json: object): string

Takes an object parsed from JSON and outputs CSV string.

### csv2Json(csv: string): object

Takes a CSV string and outputs an object ready for stringifying to JSON.

### separator: string = '.'

The separator used for separating key levels in CSV.

### diffCsv(oldCsv: string, newCsv: string, originalCsv?: string): string

Takes two CSV strings and outputs a CSV string with an extra `"CHANGED"` column. If the `original` argument is provided, labels with matching keys will be added as an extra column in the output, to aid translators.

## Known issues

* Line breaks in strings are not currently supported.
* Arrays are not currently supported.

## License

MIT

## Changes

0.1.0 Initial version.

0.1.1 Added license.

0.2.0 diffCsv.