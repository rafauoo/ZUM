# CustomDecisionTreeClassifier

`CustomDecisionTreeClassifier` to rozszerzona, interaktywna implementacja drzewa decyzyjnego zgodna z API `scikit-learn`. Umożliwia dynamiczny wybór cech na podstawie jakości podziałów, preferencji użytkownika oraz interakcji w czasie budowy drzewa.

## Cechy

- Obsługa cech **ciągłych** i **kategorycznych**
- Możliwość ograniczenia:
  - głębokości drzewa (`max_depth`)
  - minimalnej liczby próbek do podziału (`min_samples_split`)
- Heurystyka wyboru cechy z uwzględnieniem:
  - progu podobieństwa (`similarity_threshold`)
  - listy preferencji (`preference_list`)
- **Tryb interaktywny**, który umożliwia użytkownikowi ręczny wybór cechy przy zbliżonej jakości podziałów (`interactive`)
- Czytelna **wizualizacja drzewa** w konsoli dzięki bibliotece `rich`
- Obsługa nazw cech i klas (`feature_names`, `class_names`)

## Przykład użycia

```python
from your_module import CustomDecisionTreeClassifier

clf = CustomDecisionTreeClassifier(
    max_depth=4,
    interactive=True,
    feature_names=['wiek', 'płeć', 'dochód'],
    class_names=['Nie', 'Tak']
)

clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)

clf.console.print(clf.to_rich())
```

## Wymagania

- `scikit-learn`
- `numpy`
- `pandas`
- `rich`
- `IPython` (do `clear_output` w trybie interaktywnym)

Instalacja zależności:

```bash
pip install scikit-learn numpy pandas rich ipython
```

## Uwagi

- Cechy kategoryczne powinny być typu `object` lub `category` (np. w `pandas.DataFrame`)
- `predict_proba()` obsługuje tylko przypadek binarnej klasyfikacji
- Jeśli `interactive=True`, w czasie trenowania użytkownik może wybrać cechę spośród kandydatów o zbliżonej jakości
