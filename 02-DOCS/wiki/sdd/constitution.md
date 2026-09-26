---
type: constitution
title: RotulA4 — Constitution
description: Principios no negociables que rige cada fase de desarrollo en RotulA4.
tags: [sdd, constitution]
timestamp: 2026-09-26T23:47:00Z
topic: sdd
version: v1.0.0
---

# RotulA4 — Constitución del Proyecto

> Versión: v1.0.0 · Ratificada: 2026-09-26 · Última enmienda: 2026-09-26  
> Principios y convenciones no negociables del proyecto RotulA4 (Sistema de Generación e Impresión de Etiquetas Web en hojas A4).

---

## 1. Stack Canon

1. **Backend y Runtime:** Node.js (JavaScript ES6+), servidor Express (`package.json`). Empaquetado portable con script de compilación a ejecutable (`build-exe.js` / `pkg`).
2. **Frontend:** HTML5 semántico, CSS3 limpio y JavaScript nativo modular (`public/`). Sin frameworks pesados innecesarios; preserva portabilidad y ligereza.
3. **Persistencia:** SQLite (`database.js`, `etiquetas.db`).
4. **Testing:** Jest con `supertest` para pruebas unitarias y de integración de endpoints y base de datos.

---

## 2. Calidad y Manejo de Errores

5. **Manejo de Errores en Backend:**
   * Toda operación asíncrona y consulta a SQLite debe ejecutarse dentro de un bloque `try/catch`.
   * Middleware centralizado en Express para captura global de excepciones.
   * Formato unificado de respuesta de error en JSON: `{ "error": "Mensaje legible" }`.
   * **Prohibido el uso de `console.log` en código de producción final.** Usar logging estructurado y limpio.
6. **Manejo de Errores en Frontend:**
   * Todas las peticiones `fetch` deben capturarse con `try/catch`.
   * Mostrar alertas o mensajes amigables y comprensibles en la UI; nunca exponer trazas de error técnico o detalles internos del backend al usuario.
7. **Pruebas y Verificación:**
   * Todo nuevo módulo, servicio o endpoint de API debe contar con pruebas unitarias o de integración.
   * Las pruebas deben ejecutarse y pasar con éxito antes de dar cualquier tarea por concluida.

---

## 3. Convenciones de Código y Arquitectura

8. **Nomenclatura:** Uso estricto de `camelCase` para variables, funciones, métodos y propiedades de objetos.
9. **Arquitectura Modular:** Separación clara entre rutas, controladores, servicios y acceso a datos. No mezclar lógica de negocio directamente en los manejadores de ruta HTTP.

---

## 4. Flujo de Trabajo, Git y Autoría

10. **Autoría Humana:** Los commits y cambios en el repositorio son autoría del desarrollador humano. No incluir firmas automáticas de IA ni co-autorías generadas.
11. **Estabilidad del Sistema:** Ninguna modificación debe alterar o romper las plantillas, medidas de impresión A4 ni el flujo de subida y procesamiento de Excel existentes sin especificación previa.

---

## 5. Decisiones y Registro

12. Toda decisión arquitectónica o de cambio relevante debe registrarse en `02-DOCS/wiki/harness/decisions.md` o en las especificaciones de fase correspondientes.

---

## Definition of Done (Criterios de Aceptación)

Una tarea o cambio se considera completado únicamente cuando:

- [ ] Convenciones de nomenclatura (`camelCase`) y modularidad respetadas (principios 8-9).
- [ ] Operaciones asíncronas y consultas SQL envueltas en `try/catch` con formato `{ "error": "..." }` (principio 5).
- [ ] Cero `console.log` residuales en código de producción (principio 5).
- [ ] Pruebas unitarias o de integración verificadas (principio 7).
- [ ] UI con feedback amigable sin exposición de errores técnicos (principio 6).
- [ ] Funcionalidad de impresión y plantillas A4 verificada sin regresiones (principio 11).
- [ ] Decisión registrada si introdujo cambios de alcance (principio 12).

---

## Registro de Enmiendas (Append-Only)

| Fecha | Versión | Cambio | Motivo |
|---|---|---|---|
| 2026-09-26 | v1.0.0 | Constitución inicial ratificada integrando reglas de `.agagent/rules.md`. | Puesta en marcha del arnés RSC. |
